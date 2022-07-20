---
title: /riddles
position_number: 3.1
type: post
description: To add a new riddle to the database

content_markdown: |-
  📌 To add a new riddle to the database

    | HTTP Method | Endpoint | Summary                           |
    | ----------- | -------- | --------------------------------- |
    | `POST`      | /riddles | Adds a new riddle to the database |

    Use the JSON request body to add a new Riddle object to the database.

    The request body should use the following schema:
    
    | Field    | Type   | Required | Description                                                                                                                                                                                               |
    | -------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | riddle   | string | Required | The riddle's question                                                                                                                                                                                     |
    | answer   | string | Required | The riddle's answer                                                                                                                                                                                       |
    | category | string | Required | A one-word classification of the riddle. It should not contain spaces. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
    | source   | string | Optional | The source of the riddle

    {: .error }
    **Note**: The `Content-Type` header should be set to `application/json`.

    {: .success }
  **Example request**

    A curl request to add a new riddle:

    ```
    curl -X POST \
    'https://riddlesapidoc.vercel.app/riddles' \
    -H 'Content-Type: application/json' \
    -d '{
    "riddle": "There'\''s only one word in the dictionary that'\''s spelled wrong. What is it?",
    "answer": "The word '\''wrong.'\'' It'\''s the only word that'\''s spelled W-R-O-N-G.",
    "category": "kids",
    "source": "https://www.prodigygame.com/main-en/blog/riddles-for-kids/"
    }'
    ```

    A successful response will return an HTTP status code of `201` and have the following schema:

    | Field   | Type   | Description                        |
    | ------- | ------ | ---------------------------------- |
    | message | string | A brief success message            |
    | content | object | Top-level containing Riddle object |

    Where the Riddle object has this schema:

    | Field    | Type   | Description                                                                                                                                                        |
    | -------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | \_id     | string | The database id for the Riddle object                                                                                                                              |
    | riddle   | string | The riddle's question                                                                                                                                              |
    | answer   | string | The riddle's answer                                                                                                                                                |
    | category | string | A classification of the riddle. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
    | source   | string | The source of the riddle                                                                                                                                           |
    | \_\_v    | number | An internal versioning number used by Mongoose (the Object Data Model library used to connect to the MongoDB database).

    {: .success }
    **Example response**

    **Example response**

    A successful response to a `POST` request is an object like below:

    ```
    HTTP/1.1 201 Created
    Content-Type: application/json; charset=utf-8

    {
    "message": "Successfully added new riddle",
    "content": {
        "_id": "60bd0708d7dcc31bd9376abe",
        "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
        "answer": "A candle",
        "category": "easy",
        "source": "https://parade.com/947956/parade/riddles/",
        "__v": 0
    }
    }
    ```

    {: .error }
    **Possible error responses**

    A `POST` request to the /riddles endpoint may return the following errors.

    | Error code | Description                                                                                                                                |
    | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
    | 400        | `Bad Request`: This error will be returned if a required field in the request body is missing or if the `category` field contains a space. |
    | 500        | `Internal Server Error`: An unexpected error occurred on the server.

right_code_blocks:
  - code_block: |-
      curl -X POST \
        'https://riddlesapidoc.vercel.app/riddles' \
        -H 'Content-Type: application/json' \
        -d '{
        "riddle": "There'\''s only one word in the dictionary that'\''s spelled wrong. What is it?",
        "answer": "The word '\''wrong.'\'' It'\''s the only word that'\''s spelled W-R-O-N-G.",
        "category": "kids",
        "source": "https://www.prodigygame.com/main-en/blog/riddles-for-kids/"
        }'
    title: curl
    language: bash
  - code_block: |2-
      
        {
        "message": "Successfully added new riddle",
        "content": {
            "_id": "60bd0708d7dcc31bd9376abe",
            "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
            "answer": "A candle",
            "category": "easy",
            "source": "https://parade.com/947956/parade/riddles/",
            "__v": 0
        }
        }

    title: Response
    language: json
  - code_block: |2-
      {
        "error": 400,
        "message": "Bad Request"
      }
      {
        "error": 500,
        "message": "Internal Server Error"
      }
    title: Error
    language: json
---
