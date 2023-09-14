## テーブル

### items テーブル

| Column           | Type    | Options                              |
|------------------|---------|--------------------------------------|
| id               | Integer | Primary Key, Auto Increment          |
| username         | String  |                                      |
| encrypted_password | String |                                      |
| email            | String  |                                      |
| name_kanji_1     | String  |                                      |
| name_kanji_2     | String  |                                      |
| name_katakana_1  | String  |                                      |
| name_katakana_2  | String  |                                      |
| hbd              | Date    |                                      |

### users テーブル

| Column              | Type   | Options |
|---------------------|--------|---------|
| id                  | Integer| Primary Key, Auto Increment |
| product_name        | String |         |
| description_of_item | Text   |         |
| category            | String |         |
| product_condition   | String |         |
| burden_of_shipping  | String |         |
| region_of_origin    | String |         |
| shipping_days       | String |         |
| price               | Integer|         |
| user_id             | Integer| Foreign Key |
| buyer_id            | Integer| Foreign Key |
| category_id         | Integer| Foreign Key |
| brand_id            | Integer| Foreign Key |

### buys テーブル

| Column              | Type   | Options |
|---------------------|--------|---------|
| id                  | Integer| Primary Key, Auto Increment |
| buyer_user_id       | Integer|         |

### knowledges テーブル

| Column           | Type    | Options                              |
|------------------|---------|--------------------------------------|
| id               | Integer | Primary Key, Auto Increment          |
| post_code        | String  |                                      |
| prefecture_id    | Integer | Foreign Key (ActiveHash: prefectures) |
| municipality     | String  |                                      |
| street_address   | String  |                                      |
| building_name    | String  |                                      |
| phone_number     | String  | Not Null                             |
| purchase_history_id | Integer | Foreign Key (purchase_histories テーブルと関連付け) |