---
title: /riddles/{category}
position_number: 1.1
type: get
description: To get all riddles from a specific category

content_markdown: |-
  📌 To get all riddles from a specific category

    | HTTP Method | Endpoint            | Summary                                      |
    | ----------- | ------------------- | -------------------------------------------- |
    | `GET`       | /riddles/{category} | Returns all riddles from a specific category |

    Pass the desired category as a path parameter in the request. An array of Riddle objects matching the specific category is returned.

    The path parameter is defined as:

    | Parameter | Type   | Required | Description                                                                                                                                             |
    | --------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | category  | string | Required | A riddle category. The seed data (the initial riddles added to the database) include the following categories: easy, hard, funny, kids, math, and word. 


    {: .success }
  **Example request**

    A curl request to get all riddles from the _easy_ category:

    ```
    curl -X GET 'https://riddlesapidoc.vercel.app/riddles/easy'
    ```

    **Example response**

    A successful response is an array of Riddle objects:

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json; charset=utf-8
    [
    {
        "_id": "60bd0708d7dcc31bd9376abe",
        "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
        "answer": "A candle",
        "category": "easy",
        "source": "https://parade.com/947956/parade/riddles/"
    }
    ]
    ```
    The Riddle objects returned use this schema:

    | Field    | Type   | Description                                                                                                                                                        |
    | -------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | \_id     | string | The database id for the Riddle object                                                                                                                              |
    | riddle   | string | The riddle's question                                                                                                                                              |
    | answer   | string | The riddle's answer                                                                                                                                                |
    | category | string | A classification of the riddle. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
    | source   | string | The source of the riddle                                                                                                                                           |

    **Possible error responses**

    A `GET` request to the /riddles/{category} endpoint may return the following errors:

    | Error code | Description                                                                                                     |
    | ---------- | --------------------------------------------------------------------------------------------------------------- |
    | 404        | `Not Found`: This error will be returned if there are no riddles with the requested `category` in the database. |
    | 500        | `Internal Server Error`: An unexpected error occurred on the server.                                            |

right_code_blocks:
  - code_block: |-
      curl -X GET 'https://riddlesapidoc.vercel.app/riddles/easy'
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
