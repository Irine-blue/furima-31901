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
- has_many :item_purchases

## destinations テーブル

| Column           | Type    | Options                        |
| ---------------- | ------- | ------------------------------ |
| item_purchase_id | integer | null: false, foreign_key: true |
| post_code        | string  | null: false                    |
| prefecture_id    | integer | null: false                    |
| city             | string  | null: false                    |
| address          | string  | null: false                    |
| building_name    | string  |                                |
| phone_number     | string  | null: false                    |

### Association

- belongs_to :item_purchase
- belongs_to_active_hash :prefecture

## products テーブル

| Column           | Type    | Options                        |
| ---------------- | --------| ------------------------------ |
| name             | string  | null: false                    |                  |
| price            | integer | null: false                    |
| description      | text    | null: false                    |
| status_id        | integer | null: false                    |
| type_id          | integer | null: false                    |
| shipping_cost_id | integer | null: false                    |
| shipping_days_id | integer | null: false                    |
| prefecture_id    | integer | null: false                    |
| user_id          | integer | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :item_purchase

## item_purchaseテーブル

| Column     | Type    | Options                       |
| ---------- | --------| ----------------------------- |
| product_id | integer | null: false, foreign_key:true |                  |
| user_id    | integer | null: false, foreign_key:true |

### Association

- belongs_to :user
- belongs_to :product
- has_one :destination
