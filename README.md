# Chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :messages
- has_many :groups
- has_many :groups through: group_users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|content|text||
|image|text||
|user|reference|foreign_key: true|
|group|reference|foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users through: group_users

## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|reference|foreign_key: true|
|group|reference|foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user