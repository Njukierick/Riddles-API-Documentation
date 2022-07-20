---
title: /riddles
position_number: 3.4
type: patch
description: To update an existing riddle by overwriting

content_markdown: |-
  📌 To update a field of an existing riddle

    | HTTP Method | Endpoint | Summary                                               |
    | ----------- | -------- | ----------------------------------------------------- |
    | `PATCH`     | /riddles | Updates individual fields of a riddle in the database |

    Select a Riddle object to update by setting the query parameter to its `id`. Use the JSON request body to set one or more fields to a new value. Omitted fields retain their values. Currently, updating seed data (the initial riddles added to the database) is not allowed.

    The query parameter is defined as:

    | Parameter | Type   | Required | Description                                                                                                                                     |
    | --------- | ------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
    | id        | string | Required | The database `id` for the riddle. This is needed for `PUT`, `PATCH`, or `DELETE` requests which are operations performed on an existing riddle. |

    The request body should use the following schema:

    | Field    | Type   | Required | Description                                                                                                                                                                                                                     |
    | -------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | riddle   | string | Optional | An update to the riddle's question                                                                                                                                                                                              |
    | answer   | string | Optional | An update to the riddle's answer                                                                                                                                                                                                |
    | category | string | Optional | An update to the classification of the riddle. It should be one-word and not contain spaces. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
    | source   | string | Optional | An update to the source of the riddle

    {: .error }
    **Note**: The `Content-Type` header should be set to `application/json`.

    {: .success }
    **Example request**

    A curl request to update a field of a riddle:

    ```
    curl -X PATCH \
    'http://riddlesapidoc.vercel.app/riddles?id=60bd0708d7dcc31bd9376abe' \
    -H 'Content-Type: application/json' \
    -d '{
    "riddle": "There'\''s only one word in the dictionary that'\''s spelled wrong. What is it?",
    "answer": "The word '\''wrong.'\'' It'\''s the only word that'\''s spelled W-R-O-N-G.",
    "category": "kids",
    "source": "https://www.prodigygame.com/main-en/blog/riddles-for-kids/"
    }'
    ```

    A successful response will return an HTTP status code of `200` and have the following schema:

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

    {: .success }
    **Example response**

    A successful response to a `PATCH` request is an object like below:

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json; charset=utf-8

    {
    "message": Successfully updated riddle",
    "content": {
        "_id": "60bd0708d7dcc31bd9376abe",
        "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
        "answer": "A candle",
        "category": "easy",
        "source": "https://parade.com/947956/parade/riddles/",
    }
    }
    ```

    {: .error }
    **Possible error responses**

    A `PATCH` request to the /riddles endpoint may return the following errors:

    | Error code | Description                                                                                                                                |
    | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
    | 400        | `Bad Request`: This error will be returned if a required field in the request body is missing or if the `category` field contains a space. |
    | 403        | `Forbidden`: This error will be returned if you try to modify the seed data (the initial riddles added to the database).                   |
    | 404        | `Not Found`: This error will occur if the requested riddle `id` is not found in the database.                                              |
    | 500        | `Internal Server Error`: An unexpected error occurred on the server.

right_code_blocks:
  - code_block: |-
      curl -X PATCH \
        'http://riddlesapidoc.vercel.app/riddles?id=60bd0708d7dcc31bd9376abe' \
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
      
        HTTP/1.1 200 OK
        Content-Type: application/json; charset=utf-8

        {
        "message": Successfully updated riddle",
        "content": {
            "_id": "60bd0708d7dcc31bd9376abe",
            "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
            "answer": "A candle",
            "category": "easy",
            "source": "https://parade.com/947956/parade/riddles/",
        }
        }

    title: Response
    language: json
  - code_block: |2-
      {
        "error": 400,
        "message": "Bad request"
      }
      {
        "error": 403,
        "message": "forbidden"
      }
      {
        "error": 404,
        "message": "Not found"
      }
      {
        "error": 500,
        "message": "Internal Server Error"
      }
    title: Error
    language: json
---
