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

## usersテーブル
|Column|Type|Options|
|------|----|-------|
username|string|null: false|
password|string|null: false|
e-mail_address|string|priomar_key: false, null: false|
texts|text||
### Association
user belongs_to :groups
user has_many :messages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
groupname|string|
texts|text||
### Association
group belongs_to :users
group has_many :messages

## user_groupテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true, |
|group_id|integer|null: false, foreign_key: true, |
### Association
user has many :groups, through: :user_group
group has many :users, through: :user_group

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
texts|text|null: false|
images|references||
posttime|datetime|null: false|
### Association
message belongs_to :user
message belongs_to :group