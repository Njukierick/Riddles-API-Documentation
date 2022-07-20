---
title: /riddles
position_number: 3.2
type: delete
description: To delete a riddle from the database

content_markdown: |-
  📌 To delete a riddle from the database

    | HTTP Method | Endpoint | Summary                            |
    | ----------- | -------- | ---------------------------------- |
    | `DELETE`    | /riddles | Deletes a riddle from the database |

    Select a Riddle object to delete by setting the query parameter to its `id`. Currently, deleting seed data (the initial riddles added to the database) is not allowed.

    The query parameter is defined as:

    | Parameter | Type   | Required | Description                                                                                                                                     |
    | --------- | ------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
    | id        | string | Required | The database `id` for the riddle. This is needed for `PUT`, `PATCH`, or `DELETE` requests which are operations performed on an existing riddle. |

    {: .success }
  **Example request**

    A curl request to delete a riddle:

    ```
    curl -X DELETE 'https://riddlesapidoc.vercel.app/riddles?id=60bc3adb1e6946b94ca7a70a'
    ```

    A successful response will return an HTTP status code of `200` and have the following schema:

    | Field   | Type   | Description             |
    | ------- | ------ | ----------------------- |
    | message | string | A brief success message |


    {: .success }
  **Example response**

  A successful response to a DELETE request:

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json; charset=utf-8

    {
    "message": Successfully deleted riddle"
    }
    ```

    {: .error }
    **Possible error responses**

    A `DELETE` request to the /riddles endpoint may return the following errors:

    | Error code | Description                                                                                                              |
    | ---------- | ------------------------------------------------------------------------------------------------------------------------ |
    | 403        | `Forbidden`: This error will be returned if you try to delete the seed data (the initial riddles added to the database). |
    | 404        | `Not Found`: This error will occur if the requested riddle `id` is not found in the database.                            |
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
