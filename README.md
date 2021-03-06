# データベース設計

## users table
| Column |  Type  |          Options          |
|--------|--------|---------------------------|
| name   | string | null: false, unique: true |
| mail   | string | null: false, unique: true |

### Association
- has_many :groups, through :groups_users
- has_many :groups_users
- has_many :messages


## messages table
|  Column  |   Type   |            Options            |
|----------|----------|-------------------------------|
| content  | text     |                               |
| image    | text     |                               |
| user_id  | interger | null: false,foreign_key: true |
| group_id | interger | null: false,foreign_key: true |

### Association
- belongs_to :user
- belongs_to :group

## group table
| Column |  Type  |         Options          |
|--------|--------|--------------------------|
| name   | string | null: false,unique: true |

### Association
- has_many :users, through :groups_users
- has_many :groups_users
- has_many :messages

## groups_users
|  Column  |   Type  |            Options             |
|----------|---------|--------------------------------|
| user_id  | integer | null: false,foreign_key: true |
| group_id | integer | null: false,foreign_key: true |

### Association
- belongs_to :user
- belongs_to :group
