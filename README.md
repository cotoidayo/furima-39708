## テーブル

### users テーブル

| カラム名             | データ型 | オプション                     |
|---------------------|--------|------------------------------|
| id                  | integer| Primary Key, Auto Increment |
| username            | string | null: false                  |
| encrypted_password  | string | null: false                  |
| email               | string | null: false, unique: true    |
| name_kanji_1        | string | null: false                  |
| name_kanji_2        | string | null: false                  |
| name_katakana_1     | string | null: false                  |
| name_katakana_2     | string | null: false                  |
| hbd                 | date   | null: false                  |

class User < ApplicationRecord
  has_many :items, foreign_key: 'seller_id'
  has_many :buys, foreign_key: 'buyer_user_id'
end

### items テーブル

| カラム名             | データ型 | オプション                     |
|---------------------|--------|------------------------------|
| id                  | integer| Primary Key, Auto Increment |
| product_name        | string | null: false                  |
| description_of_item | text   |                              |
| category            | string |                              |
| product_condition   | string |                              |
| burden_of_shipping  | string |                              |
| region_of_origin    | string |                              |
| shipping_days       | string |                              |
| price               | integer|                              |

class Item < ApplicationRecord
  belongs_to :seller, class_name: 'User'
  has_one :buy
end

### buys テーブル

| カラム名             | データ型 | オプション                     |
|---------------------|--------|------------------------------|
| id                  | integer| Primary Key, Auto Increment |
| buyer_user_id       | integer| null: false                  |

class Buy < ApplicationRecord
  belongs_to :item
  belongs_to :buyer_user, class_name: 'User', foreign_key: 'buyer_user_id'
end



### knowledges テーブル

| カラム名             | データ型 | オプション                     |
|---------------------|--------|------------------------------|
| id                  | integer| Primary Key, Auto Increment |
| post_code           | string | null: false                  |
| prefectures         | string | null: false                  |
| municipalities      | string |                              |
| street_address      | string |                              |
| building_name       | string |                              |
| phone_number        | string | null: false                  |

class Knowledge < ApplicationRecord
  belongs_to :buy
end
