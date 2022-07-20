---
title: /riddles/random
position_number: 2.0
type: get
description: To select a random riddle from the entire database

content_markdown: |-
  📌 To select a random riddle from the entire database:

    | HTTP Method | Endpoint        | Summary                 |
    | ----------- | --------------- | ----------------------- |
    | `GET`       | /riddles/random | Returns a random riddle |

    Make a `GET` request. A random Riddle object from the entire database is selected and returned.

        The path parameter is defined as:

        | Parameter | Type   | Required | Description                                                                                                                                             |

    {: .success }
  **Example request**

    A curl request to get a random riddle:

    ```
    curl -X GET 'https://riddlesapidoc.vercel.app/riddles/random'
    ```
    {: .success }
  **Example response**
    A successful response will return an HTTP status code of `200`. The Riddle object returned uses this schema:

    | Field    | Type   | Description                                                                                                                                                        |
    | -------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | \_id     | string | The database id for the Riddle object                                                                                                                              |
    | riddle   | string | The riddle's question                                                                                                                                              |
    | answer   | string | The riddle's answer                                                                                                                                                |
    | category | string | A classification of the riddle. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
    | source   | string | The source of the riddle  

    {: .success }
    **Example response**

    A successful response is an individual Riddle object:

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json; charset=utf-8

    {
    "_id": "60bd0708d7dcc31bd9376abe",
    "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
    "answer": "A candle",
    "category": "easy",
    "source": "https://parade.com/947956/parade/riddles/"
    }
    ```

    {: .error }
    **Possible error responses**

    A `GET` request to the /riddles/random endpoint may return the following errors:

    | Error code | Description                                                                       |
    | ---------- | --------------------------------------------------------------------------------- |
    | 404        | `Not Found`: This error will be returned if there are no riddles in the database. |
    | 500        | `Internal Server Error`: An unexpected error occurred on the server.              |

right_code_blocks:
  - code_block: |-
      curl -X GET 'https://riddlesapidoc.vercel.app/riddles/random'
    title: curl
    language: bash
  - code_block: |2-
      
        {
        "_id": "60bd0708d7dcc31bd9376abe",
        "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
        "answer": "A candle",
        "category": "easy",
        "source": "https://parade.com/947956/parade/riddles/"
         }

    title: Response
    language: json
  - code_block: |2-
      {
        "error": 404,
        "message": "Not Found"
      }
      {
        "error": 500,
        "message": "Internal Server Error"
      }
    title: Error
    language: json
---
