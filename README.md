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

class User < ApplicationRecord
  has_many :items, foreign_key: 'seller_id'
  has_many :purchases, foreign_key: 'buyer_id'
end

### items テーブル

| カラム名            | データ型 | オプション                        |
|---------------------|----------|-----------------------------------|
| id                  | integer  | Primary Key, Auto Increment      |
| product_name        | string   | null: false                       |
| description_of_item | text     |                                   |
| category_id         | integer  |                                   |
| product_condition   | integer  |                                   |
| burden_of_shipping  | integer  |                                   |
| region_of_origin    | integer  |                                   |
| shipping_days       | integer  |                                   |
| price               | integer  |                                   |
| seller_id           | integer  | Foreign Key (users テーブルと関連付け) |


class Item < ApplicationRecord
  belongs_to :seller, class_name: 'User', foreign_key: 'seller_id'
  has_one :purchase
  belongs_to :category, class_name: 'Category', foreign_key: 'category_id'
  belongs_to :condition, class_name: 'Condition', foreign_key: 'product_condition'
  belongs_to :shipping, class_name: 'Shipping', foreign_key: 'burden_of_shipping'
  belongs_to :region, class_name: 'Region', foreign_key: 'region_of_origin'
  belongs_to :days, class_name: 'ShippingDay', foreign_key: 'shipping_days'
end



### knowledges テーブル

| カラム名          | データ型 | オプション                        |
|-------------------|----------|-----------------------------------|
| id                | integer  | Primary Key, Auto Increment      |
| post_code         | string   | null: false                       |
| prefectures_id    | integer  |                                   |
| municipalities    | string   |                                   |
| street_address    | string   |                                   |
| building_name     | string   |                                   |
| phone_number      | string   | null: false                       |
| buyer_id          | integer  | Foreign Key (users テーブルと関連付け) |
| item_id           | integer  | Foreign Key (items テーブルと関連付け) |

class Purchase < ApplicationRecord
  belongs_to :buyer, class_name: 'User', foreign_key: 'buyer_id'
  belongs_to :item
end






### buys テーブル

| カラム名     | データ型 | オプション                        |
|--------------|----------|-----------------------------------|
| id           | integer  | Primary Key, Auto Increment      |
| name         | string   | null: false                       |

class Category < ApplicationRecord
  has_many :items, foreign_key: 'category_id'
end