# 🌐 Open Arts API
A general purpose visual arts API built to act as a free open-ended resource for any number of independantly developed applications geared towards serving practicing artists, art students and the broader arts community.

### Core CRUD Functionality for...
1) Individual Artists
2) Individual Artworks
3) Galleries / Exhibition Spaces
4) Exhibitions / Art Shows

### StudioSwipe App CRUD Functionality for...
1) Users
1) Artist Matches
2) Conversations
3) Messages

<br/><br/>

# Core Schema / Database Tables


<br/>

## Users Table
(separate from artists etc to accomodate other apps and gallerists etc)

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `first_name`        | string         | not null, indexed               |
| `last_name`         | string         | not null, indexed               |
| `email`             | string         | not null, indexed               |
| `password_digest`   | string         | not null                        |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |


<br/>

## Artists Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `user_id`           | integer        | indexed, foreign key            |
| `first_name`        | string         | not null, indexed               |
| `middle_name`       | string         |                                 |
| `last_name`         | string         | not null, indexed               |
| `birth_date`        | datetime       | not null, indexed               |
| `death_date`        | datetime       |                                 |
| `birth_city`        | string         | not null, indexed               |
| `death_city`        | string         |                                 |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Degrees Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `school_id`         | integer        | not null, indexed, foreign key  |
| `degree_type`       | string         | not null, indexed               |
| `concentration`     | string         | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Artists-to-Degrees Reference Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `artist_id`         | integer        | not null, indexed, foreign key  |
| `degree_id`         | integer        | not null, indexed, foreign key  |
| `start_date`        | datetime       | not null                        |
| `end_date`          | datetime       | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Art Schools Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `school_name`       | string         | not null, indexed               |
| `city`              | string         | not null, indexed               |
| `country`           | string         | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Artworks Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `title`             | string         | not null, indexed               |
| `height_mm`         | string         | not null, indexed               |
| `width_mm`          | datetime       | not null                        |
| `depth_mm`          | datetime       | not null                        |
| `length_sec`        | datetime       | not null                        |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Artworks-to-Mediums Joins Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, primary key           |
| `artwork_id`        | integer        | not null, indexed, foreign key  |
| `medium_id`         | integer        | not null, indexed, foreign key  |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Mediums Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `medium_name`       | string         | not null, indexed, unique       |
| `medium_type`       | string         | not null, indexed, (ie: 2D)     |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Exhibition Spaces Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `name`              | string         | not null, indexed               |
| `city`              | string         | not null, indexed               |
| `state_province`    | string         | not null, indexed               |
| `country`           | string         | not null, indexed               |
| `address`           | string         | not null                        |
| `phone`             | string         |                                 |
| `founding_date`     | datetime       | not null                        |
| `closing_date`      | datetime       |                                 |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Weblinks Table
(necessary to distinguish between primary websites and social media sites etc)

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `foreign_id`        | string         | not null, indexed               |
| `foreign_id_type`   | string         | not null, indexed, artist / gallery etc               |
| `link_type`         | string         | not null, indexed, social media / personal etc        |
| `platform_name`     | string         | not null, indexed               |
| `weblink_url`       | string         | not null, indexed               |
| `platform_type`     | string         | not null                        |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Artists-to-Galleries Representation Reference Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `artist_id`         | string         | not null, indexed               |
| `artspace_id`       | string         | not null, indexed               |
| `start_date`        | datetime       | not null                        |
| `end_date`          | datetime       |                                 |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Art Events Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `event_title`       | string         | not null, indexed               |
| `artspace_id`       | string         | not null, indexed               |
| `reception_date`    | datetime       | not null                        |
| `open_date`         | datetime       | not null                        |
| `close_date`        | datetime       |                                 |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Events-to-Artworks Joins Table
(when specific artwork is known)

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `event_id`          | string         | not null, indexed               |
| `artwork_id`        | string         | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Events-to-Artist Joins Table
(when only artist known, redundant if artwork is known)

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `event_id`          | string         | not null, indexed               |
| `artist_id`         | string         | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Prices Table
(separate from artworks to track multiple prices over time)

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `artwork_id`        | string         | not null, indexed               |
| `price`             | string         | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/>

## Sales Table

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `artwork_id`        | string         | not null, indexed               |
| `sale_price`        | string         | not null, indexed               |
| `sale_currency`     | string         | not null, indexed               |
| `seller_type`       | string         | indexed                         |   
| `seller_id`         | string         | indexed                         |
| `seller_name`       | string         | indexed                         |  
| `sale_date`         | datetime       | not null                        |
| `created_at`        | datetime       | not null                        |
| `author_id`         | integer        | not null, foreign key           |


<br/><br/>

# Studio Swipe App Schema / Database Tables


<br/>

## Studio_Swipe Users Table
(separate from artists etc to accomodate other apps and gallerists etc)

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `user_id`           | integer        | not null, indexed, foreign key  |
| `user_name`         | string         | not null, indexed               |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |



<br/>

## Studio_Swipe Matches Table
(separate from artists etc to accomodate other apps and gallerists etc)

| Column Name         | Data Type      | Details                         |
|---------------------|----------------|---------------------------------|
| `id`                | integer        | not null, indexed, primary key  |
| `liker_user_id`     | integer        | not null, indexed, foreign key  |
| `liked_user_id`     | string         | not null, indexed, foreign key  |
| `created_at`        | datetime       | not null                        |
| `updated_at`        | datetime       |                                 |





