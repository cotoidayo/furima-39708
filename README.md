## データベース設計

このREADMEでは、データベースの設計情報を提供します。

### users テーブル

| カラム名           | データ型 | オプション                        |
|--------------------|----------|-----------------------------------|
| id                 | integer  | Primary Key, Auto Increment      |
| username           | string   | null: false                       |
| encrypted_password | string   | null: false                       |
| email              | string   | null: false, unique: true         |
| first_name         | string   | null: false                       |
| last_name          | string   | null: false                       |
| first_name_kana    | string   | null: false                       |
| last_name_kana     | string   | null: false                       |
| birthday           | date     | null: false                       |

#### アソシエーション

- has_many :items, foreign_key: 'seller_id'
- has_many :buys, foreign_key: 'buyer_id'

### items テーブル

| カラム名            | データ型 | オプション                        |
|---------------------|----------|-----------------------------------|
| id                  | integer  | Primary Key, Auto Increment      |
| product_name        | string   | null: false                       |
| description_of_item | text     | null: false                                  |
| category_id         | references | null: false                                  |
| product_condition_id| references| null: false                       |
| burden_of_shipping_id| references| null: false                       |
| region_of_origin_id  | references| null: false                       |
| shipping_days_id     | references| null: false                       |
| price               | integer  | null: false                       |
| seller_id           | integer  | Foreign Key (users テーブルと関連付け) |

#### アソシエーション

- belongs_to :seller, class_name: 'User'
- belongs_to :category, class_name: 'Category', foreign_key: 'category_id'
- belongs_to :condition, class_name: 'Condition', foreign_key: 'product_condition_id'
- belongs_to :shipping, class_name: 'Shipping', foreign_key: 'burden_of_shipping_id'
- belongs_to :region, class_name: 'Region', foreign_key: 'region_of_origin_id'
- belongs_to :days, class_name: 'ShippingDay', foreign_key: 'shipping_days_id'
- has_one :purchase

### knowledges テーブル

| カラム名          | データ型 | オプション                        |
|-------------------|----------|-----------------------------------|
| id                | integer  | Primary Key, Auto Increment      |
| post_code         | string   | null: false                       |
| prefecture_id     | references | null: false                       |
| municipalities    | string   | null: false                       |
| street_address    | string   | null: false                       |
| building_name     | string   |                                   |
| phone_number      | string   | null: false                       |
| buyer_id          | integer  | Foreign Key (users テーブルと関連付け) |
| item_id           | integer  | Foreign Key (items テーブルと関連付け) |

#### アソシエーション

- belongs_to :buyer, class_name: 'User'
- belongs_to :item

### buys テーブル

| カラム名     | データ型 | オプション                        |
|--------------|----------|-----------------------------------|
| id           | integer  | Primary Key, Auto Increment      |
| user_id      | references | null: false, foreign_key: true   |
| item_id      | references | null: false, foreign_key: true   |

#### アソシエーション

- belongs_to :user
- belongs_to :item
- has_many :knowledges, foreign_key: 'buyer_id'