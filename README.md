## データベース設計

このREADMEでは、データベースの設計情報を提供します。

### users テーブル

| カラム名           | データ型 | オプション                        |
|--------------------|----------|-----------------------------------|
| id                 | integer  | Primary Key, Auto Increment      |
| username           | string   | null: false                       |
| encrypted_password | string   | null: false                       |
| email              | string   | null: false, unique: true         |
| name_kanji_1       | string   | null: false                       |
| name_kanji_2       | string   | null: false                       |
| name_katakana_1    | string   | null: false                       |
| name_katakana_2    | string   | null: false                       |
| hbd                | date     | null: false                       |
| seller_id           | integer  | Foreign Key (users テーブルと関連付け) |

  has_many :items, foreign_key: 'seller_id'
  has_many :buys, foreign_key: 'buyer_id'
  has_many :knowledges, foreign_key: 'buyer_id

### items テーブル

| カラム名            | データ型 | オプション                        |
|---------------------|----------|-----------------------------------|
| id                  | integer  | Primary Key, Auto Increment      |
| product_name        | string   | null: false                       |
| description_of_item | text     | null: false                                  |
| category_id         | integer  | null: false                                  |
| product_condition_id| integer| null: false|
| burden_of_shipping_id| integer| null: false|
| region_of_origin_id  | integer| null: false|
| shipping_days_id     | integer| null: false|
| price               | integer| null: false               |




belongs_to :user
has_one :buy
  belongs_to :category, class_name: 'Category', foreign_key: 'category_id'
  belongs_to :condition, class_name: 'Condition', foreign_key: 'product_condition'
  belongs_to :shipping, class_name: 'Shipping', foreign_key: 'burden_of_shipping'
  belongs_to :region, class_name: 'Region', foreign_key: 'region_of_origin'
  belongs_to :days, class_name: 'ShippingDay', foreign_key: 'shipping_days'




### knowledges テーブル

| カラム名          | データ型 | オプション                        |
|-------------------|----------|-----------------------------------|
| id                | integer  | Primary Key, Auto Increment      |
| post_code         | string   | null: false                       |
| prefecture_id    | integer  | null: false                                  |
| municipalities    | string   | null: false                                  |
| street_address    | string   | null: false                                  |
| building_name     | string   |                                   |
| phone_number      | string   | null: false                       |
| buy_id            | integer  | null: false, foreign_key: true |

 belongs_to :purchase_history
  belongs_to :destination, class_name: 'Knowledge', foreign_key: 'knowledge_id'
   belongs_to :buyer, class_name: 'User', foreign_key: 'buyer_id'







### buys テーブル

| カラム名     | データ型 | オプション                        |
|--------------|----------|-----------------------------------|
| id                  | integer| Primary Key, Auto Increment |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |



  has_many :items, foreign_key: 'category_id'
