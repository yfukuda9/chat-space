# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# DB設計
## users table
|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false|
|mail|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :messages
- has_many :groups_users

## groups table
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :groups_users
- has_many :messages

## messages table
|Column|Type|Options|
|------|----|-------|
|message|string|null: false|
|image|string||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## groups_users table
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreing_key: true|

### Association
- belongs_to :group
- belongs_to :user

