# chat space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|index: true,null:false, unique: true|
|Email|text|null: false, unique: true|
|password|text|null: false|
### Association
- has_many :groups,through: :users_groups
- has_many :messages
- has_many :users_groups

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false,foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :users,through::users_groups
- has_many :messages
- has_many :users_groups


## users_groupsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|null: false, foreign_key: true|
|group_id|reference|null: false, foreign_key: true|

### Association
- belongs_to :users
- belongs_to :group