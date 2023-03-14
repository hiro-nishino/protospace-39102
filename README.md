# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
|email               | string | null: UNIQUE|
| encrypted_password | string | not null    |
| name               | string | not null    |
| profile            | text   | not null    |
| occupation         | text   | not null    |
| position           | text   | not null    |
### Association

- has_many :prototypes
- has_many :comments

## prototypes テーブル

| Column   | Type        | Options                      |
| ------   | ------      | ---------------------------- |
| title    | string      | not null                     |
|catch_copy| text        | not null                     |
| concept  | text        | not null                     |
| user     | references  | not null  foreign_key: true  |
### Association

- has_many :comments
- belongs_to :user

## comments テーブル

| Column        | Type       | Options                        |
| ------        | ---------- | ------------------------------ |
| content       | text       | not null,                      |
| prototype     | references | not null,    foreign_key: true |
| user          | references | not null,    foreign_key: true |
### Association

- belongs_to :prototypes
- belongs_to :user
