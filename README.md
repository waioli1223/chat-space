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
|username|string|null: false|
|password|string|null: false|
|e-mail_address|string|priomar_key: false, null: false|
|texts|text||
### Association
belongs_to :users_groups 
has_many :groups, through: :users_groups
has_many :messages, through: :users_groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|
|texts|text||
### Association
belongs_to :users_groups, 
has_many :users, through: :users_groups
has_many :messages, through: :users_groups


## users_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
has_many :groups
has_many :users

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|texts|text|null: false|
|images|references||
|posttime|datetime|null: false|
### Association
belongs_to :users
belongs_to :groups