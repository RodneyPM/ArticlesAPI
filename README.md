# Articles API

## Usage

All responses will have the form

```json
{
    "data": "Mixed type holding the content of the response",
    "message": "Description of what happened"
}
```

Subsequent response definitions will only detail the expected value of the `data field`

### List all articles

**Definition**

`GET /articles`

**Response**

- `200 OK` on success

```json
[
    {
        "identifier": "headlines-101",
        "name": "Top Headline",
        "article_type": "news-headline",
        "article_description": "today the top neews features a lot of drama from gauteng as covid numbers continue to rise ..."
    },
    {
        "identifier": "headlines-102",
        "name": "Daily Headline",
        "article_type": "top-story",
        "article_description": "New covid variant on the rise, may people worried about the new strain as look more deadly ..."
    }
]
```

### Adding a new article

**Definition**

`POST /articles`

**Arguments**

- `"identifier":string` a globally unique identifier for this article
- `"name":string` a friendly name for this article
- `"article_type":string` the type of the article as they can be many
- `"article_description":string` article description containing text about the news featured

If article with the given identifier already exists, the existing article will be overwritten.

**Response**

- `201 Created` on success

```json
{
     "identifier": "headlines-101",
        "name": "Top Headline",
        "article_type": "news-headline",
        "article_description": "today the top neews features a lot of drama from gauteng as covid numbers continue to rise ..."
}
```

## Lookup article details

`GET /article/<identifier>`

**Response**

- `404 Not Found` if the article does not exist
- `200 OK` on success

```json
{
     "identifier": "headlines-101",
        "name": "Top Headline",
        "article_type": "news-headline",
        "article_description": "today the top neews features a lot of drama from gauteng as covid numbers continue to rise ..."
}
```

## Delete article

**Definition**

`DELETE /article/<identifier>`

**Response**

- `404 Not Found` if the article does not exist
- `204 No Content` on success
