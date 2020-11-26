# テーブル設計

## users テーブル

| Column         | Type       | Options      |
| -------------- | ---------- | -------------|
| name           | string     |  null: false |
| first_name     | string     |  null: false |
| first_name_kana| string     |  null: false |
| last_name      | string     |  null: false |
| last_name_kana | string     |  null: false |
| birthday       | string     |  null: false |
| email          | string     |  null: false, unique:true |
| password       | string     |  null:false  |

### Association

- has_many :users_items
- has_many :items, through: users_items
- has_many :logs

## items テーブル

| Column       | Type       | Options     |
| ------------ | -----------| ------------|
| item_name    | string     | null: false |
| buyer        | string     | null: false |
| image        | Active record | null: false |
| introduction | text       | null: false |
| category     | ActiveHash | null: false |
| condition    | text       | null: false |
| price        | text       | null: false |

### Association

- has_many :users_items
- has_many :users, through: users_items
- has_one  :log

## users_items テーブル

| Column | Type       | Options                        |
| ------ | ---------- | -------------------------------|
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
## logs テーブル

| Column | Type       | Options                        |
| ------ | ---------- | -------------------------------|
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one    :shippings

## shippings テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | -------------------------------|
| cost        | text       | null: false                    |
| date        | text       | null: false                    |
| post_code   | text       | null: false                    |
| prefecture  | text       | null: false                    |
| city        | text       | null: false                    |
| house_number| text       | null: false                    |
| tell        | text       | null: false                    |
| user   | references | null: false, foreign_key: true |

### Association

- belongs_to : log