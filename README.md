# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| family_name        | string | null: false               |
| first_name         | string | null: false               |
| family_name_kana   | string | null: false               |
| first_name_kana    | string | null: false               |
| birthday           | date   | null: false               |

### Association

- has_many :products
- has_many :item_purchase
- belongs_to :destination
- belongs_to :card

## destination テーブル

| Column           | Type    | Options                        |
| ---------------- | ------- | ------------------------------ |
| user_id          | integer | null: false, foreign_key: true |
| post_code        | string  | null: false                    |
| prefecture_id    | integer | null: false                    |
| city             | string  | null: false                    |
| address          | string  | null: false                    |
| building_name    | string  |                                |
| phone_number     | string  | null: false                    |

### Association

- has_many :products
- belongs_to :users
- belongs_to_active_hash :prefecture

## product テーブル

| Column        | Type    | Options                        |
| ------------- | --------| ------------------------------ |
| name          | string  | null: false                    |                  |
| price         | integer | null: false                    |
| description   | text    | null: false                    |
| status        | string  | null: false                    |
| type          | string  | null: false                    |
| shipping_cost | integer | null: false                    |
| shipping_days | integer | null: false                    |
| prefecture_id | integer | null: false                    |
| shipping_id   | integer | null: false,                   |
| user_id       | integer | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item_purchase

## item_purchaseテーブル

| Column        | Type    | Options                       |
| ------------- | --------| ----------------------------- |
| product       | integer | null: false, foreign_key:true |                  |
| user          | integer | null: false, foreign_key:true |

### Association

- belongs_to :user
- belongs_to :product
- belongs_to :

