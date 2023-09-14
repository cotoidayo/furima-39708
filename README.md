## テーブル

### users テーブル

| カラム名         | データ型 | オプション                     |
|------------------|----------|--------------------------------|
| id               | integer  | Primary Key, Auto Increment    |
| username         | string   | null: false                       |
| password         | string   | null: false                       |
| email            | string   | null: false, unique: true               |
| name_kanji_1     | string   | null: false                             |
| name_kanji_2     | string   | null: false                             |
| name_katakana_1  | string   | null: false                             |
| name_katakana_2  | string   | null: false                             |
| hbd              | date     | null: false                             |

### items テーブル

| カラム名            | データ型 | オプション                     |
|---------------------|----------|--------------------------------|
| id                  | integer  | Primary Key, Auto Increment    |
| product_name        | string   | null: false                       |
| description_of_item | text     |                                |
| category            | string   |                                |
| product_condition   | string   |                                |
| burden_of_shipping  | string   |                                |
| region_of_origin    | string   |                                |
| shipping_days       | string   |                                |
| price               | integer  |                                |

### buys テーブル

| カラム名        | データ型 | オプション                     |
|-----------------|----------|--------------------------------|
| id              | integer  | Primary Key, Auto Increment    |
| buyer_user_id   | integer  | null: false                       |

### knowledges テーブル

| カラム名          | データ型 | オプション                     |
|-------------------|----------|--------------------------------|
| id                | integer  | Primary Key, Auto Increment    |
| post_code         | string   | null: false                       |
| prefectures       | string   | null: false                       |
| municipalities    | string   |                                |
| street_address    | string   |                                |
| building_name     | string   |                                |
| phone_number      | string   | null: false                       |
