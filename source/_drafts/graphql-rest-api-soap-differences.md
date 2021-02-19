---
title: graphql-rest-soap-differences
date: 2019-07-21 20:55:30
tags:
 - api
---

##

Graphql

括號{}定義的資料結構

三次請求變成一次請求

example.com/users/{id}
example.com/users/{id}/followers
example.com/users/{id}/posts

```request
query {
    User(id: "er3tg439frjw") {
        name
        posts {
            title
        }
        followers(last: 3) {
            name
        }
    }
}
```

```response
{
  "data": {
    "User": {
      "name": "Mary",
      "posts": [
        {  title: "Learn GraphQL today" }
      ],
      "followers": [
        { name: "John" },
        { name: "Alice" },
        { name: "Sarah" },
      ]
    }
  }
}


Q1: Once the schema is defined, frontend and backend teams can work independently from one another
