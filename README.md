## データベース設計

このREADMEでは、データベースの設計情報を提供します。

### users テーブル

| カラム名            | データ型 | オプション                       |
|--------------------|----------|-------------------------------|
| id                 | integer  | Primary Key, Auto Increment   |
| username           | string   | null: false                   |
| encrypted_password | string   | null: false                    |
| email              | string   | null: false, unique: true      |
| first_name         | string   | null: false                    |
| last_name          | string   | null: false                    |
| kana_first_name    | string   | null: false                    |
| kana_last_name     | string   | null: false                    |
| hbd                | date     | null: false                    |

#### アソシエーション

- has_many :items
- has_many :buys

### items テーブル

| カラム名            | データ型   | オプション                         |
|---------------------|------------|--------------------------------|
| id                  | integer    | Primary Key, Auto Increme    |
| product_name        | string     | null: false                  |
| description_of_item | text       | null: false                   |
| category            | integer    | null: false                   |
| product_condition   | integer    | null: false                   |
| burden_of_shipping  | integer    | null: false                    |
| region_of_origin    | integer    | null: false                    |
| shipping_days       | integer    | null: false                    |
| price               | integer    | null: false                    |
| user                | references | null: false,                   |

#### アソシエーション

- belongs_to :user
- has_one :purchase
- belongs_to :category, class_name: 'Category', foreign_key: 'category_id'
- belongs_to :condition, class_name: 'Condition', foreign_key: 'product_condition_id'
- belongs_to :shipping, class_name: 'Shipping', foreign_key: 'burden_of_shipping_id'
- belongs_to :region, class_name: 'Region', foreign_key: 'region_of_origin_id'
- belongs_to :days, class_name: 'ShippingDay', foreign_key: 'shipping_days_id'

### knowledges テーブル

| カラム名        | データ型   | オプション                           |
|----------------|----------|-------------------------------------|
| id             | integer  | Primary Key, Auto Increment         |
| post_code      | string   | null: false                         |
| prefecture     | integer  | null: false                         |
| municipalities | string   | null: false                         |
| street_address | string   | null: false                         |
| building_name  | string   |                                     |
| phone_number   | string   | null: false                         |
| buy            | integer  | Foreign Key (buys テーブルと関連付け)  |

#### アソシエーション
- belongs_to :buys
### buys テーブル

| カラム名   | データ型     | オプション                        |
|-----------|------------|----------------------------------|
| id        | integer    | Primary Key, Auto Increment      |
| user      | references | null: false, foreign_key: true   |
| item      | references | null: false, foreign_key: true   |


#### アソシエーション

- belongs_to :user
- belongs_to :item
- has_one :knowledge