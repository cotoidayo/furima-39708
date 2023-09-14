## テーブル

### users テーブル

| カラム名         | データ型 | オプション                     |
|------------------|----------|--------------------------------|
| id               | integer  | Primary Key, Auto Increment    |
| username         | string   | Not Null                       |
| password         | string   | Not Null                       |
| email            | string   | Not Null, Unique                |
| name_kanji_1     | string   |                                |
| name_kanji_2     | string   |                                |
| name_katakana_1  | string   |                                |
| name_katakana_2  | string   |                                |
| hbd              | date     |                                |

### items テーブル

| カラム名            | データ型 | オプション                     |
|---------------------|----------|--------------------------------|
| id                  | integer  | Primary Key, Auto Increment    |
| product_name        | string   | Not Null                       |
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
| buyer_user_id   | integer  | Not Null                       |

### knowledges テーブル

| カラム名          | データ型 | オプション                     |
|-------------------|----------|--------------------------------|
| id                | integer  | Primary Key, Auto Increment    |
| post_code         | string   | Not Null                       |
| prefectures       | string   | Not Null                       |
| municipalities    | string   |                                |
| street_address    | string   |                                |
| building_name     | string   |                                |
| phone_number      | string   | Not Null                       |
