# Open Arts API 🌐
A general purpose visual arts API built to act as an open-ended resource for applications built to serve practicing artists, art students and the broader arts community.

## Core CRUD Functionality for...
1) Individual Artists
2) Individual Artworks
3) Galleries / Exhibition Spaces
4) Exhibitions / Art Shows

## StudioSwipe App CRUD Functionality for...
1) Users
1) Artist Matches
2) Conversations
3) Messages

# Core Schema / Database Tables

## Artists Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `first_name`        | string         | not null, indexed               |
| `middle_name`       | string         |                                 |
| `last_name`         | string         | not null, indexed               |
| `birth_date`        | datetime       | not null, indexed               |
| `death_date`        | datetime       |                                 |
| `birth_city`        | string         | not null, indexed               |
| `death_city`        | string         |                                 |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |

## Degrees Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `artist_id`         | integer        | not null, indexed, foreign key  |
| `school_id`         | integer        | not null, indexed, foreign key  |
| `degree_type`       | string         | not null, indexed               |
| `concentration`     | string         | not null, indexed               |
| `start_date`        | datetime       | not null                        |
| `end_date`          | datetime       | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


## Schools Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `school_name`       | string         | not null, indexed               |
| `city`              | string         | not null, indexed               |
| `country`           | string         | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |




• index on  `id, unique: true` <br/>
• index on  `username, unique: true` <br/>
• index on  `email, unique: true` <br/>
• index on  `session_token, unique: true` <br/>

***

## `blogs`

| Column Name       | Data Type | Details                         |
|-------------------|-----------|---------------------------------|
| `id`              | integer   | not null, indexed, primary key  |
| `title`           | string    | not null                        |
| `description`     | string    |                                 |
| `banner_pic_url`  | string    |                                 |
| `author_id`       | integer   | not null, indexed, foreign key  |
| `created_at`      | datetime  | not null                        |
| `updated_at`      | datetime  | not null                        |

• index on  `id, unique: true` <br/>
• index on  `name, unique: true` <br/>
• index on  `author_id` <br/>

***

## `posts`

| Column Name       | Data Type | Details                         |
|-------------------|-----------|---------------------------------|
| `id`              | integer   | not null, indexed, primary key  |
| `title`           | string    | not null, indexed               |
| `text`            | string    |                                 |
| `pic_url`         | string    |                                 |
| `blog_id`         | integer   | not null, indexed, foreign key  |
| `cname_path`      | string    | (might be used for DNS reroute?)|
| `created_at`      | datetime  | not null                        |
| `updated_at`      | datetime  | not null                        |

• index on  `id, unique: true` <br/>
• index on  `title` <br/>
• index on  `author_id` <br/>
