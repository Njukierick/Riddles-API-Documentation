---
title: /riddles
position_number: 1.0
type: get
description: To get all riddles or an individual riddle

content_markdown: |-
  📌 To get all riddles or an individual riddle

  | HTTP Method | Endpoint | Summary                |
  | ----------- | -------- | ---------------------- |
  | `GET`       | /riddles | Returns Riddle objects |

  {: .info }
  Use the optional `id` query parameter to have the corresponding Riddle object returned. Omit the query parameter to have an array of all the Riddle objects in the database returned.

  The optional query parameter is defined as

  | Parameter | Type   | Required | Description                                                                                                                               |
  | --------- | ------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
  | id        | string | Optional | If the database id for a riddle is known, use this parameter to get that specific Riddle object. **Omit for all riddles to be returned.** |

  {: .info }

  Lists all the photos you have access to. You can paginate by using the parameters listed above.

  {: .success }
  **Example request**


  A curl request to get _all_ riddles:
  ```
  curl -X GET 'https://riddlesapidoc.vercel.app/riddles'
  ```

  {: .success }
  **Example request**


  A successful response has an HTTP status code of `200` and is an array of Riddle objects:

  ```
    HTTP/1.1 200 OK
  Content-Type: application/json; charset=utf-8
    {
      "_id": "60bc3ffb5dcf8ac52f16a7fd",
      "riddle": "What has to be broken before you can use it?",
      "answer": "An egg",
      "category": "easy",
      "source": "https://parade.com/947956/parade/riddles/"
    },
    {
      "_id": "60bc3ffb5dcf8ac52f16a800",
      "riddle": "I'm tall when I'm young, and I'm short when I'm old. What am I?",
      "answer": "A candle",
      "category": "easy",
      "source": "https://parade.com/947956/parade/riddles/"
    }
  ```
  The Riddle object returned uses this schema:

  | Field    | Type   | Description                                                                                                                                                        |
  | -------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
  | \_id     | string | The database id for the Riddle object                                                                                                                              |
  | riddle   | string | The riddle's question                                                                                                                                              |
  | answer   | string | The riddle's answer                                                                                                                                                |
  | category | string | A classification of the riddle. The original database includes the categories: easy, hard, funny, kids, math, and word. This is not an enum and more can be added. |
  | source   | string | The source of the riddle                                                                                                                                           |

  **Possible error responses**

  A `GET` request to the /riddles endpoint may return the following errors:

  | Error code | Description                                                                                                                                 |
  | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
  | 404        | `Not Found`: This error will occur if the requested riddle `id` is not found in the database. It could also occur if the database is empty. |
  | 500        | `Internal Server Error`: An unexpected error occurred on the server.

left_code_blocks:
  - code_block: |-
      $.get("http://api.myapp.com/books/", { "token": "YOUR_APP_KEY"}, function(data) {
        alert(data);
      });
    title: jQuery
    language: javascript
  - code_block: |-
      r = requests.get("http://api.myapp.com/books/", token="YOUR_APP_KEY")
      print r.text
    title: Python
    language: python
  - code_block: |-
      var request = require("request");
      request("http://api.myapp.com/books?token=YOUR_APP_KEY", function (error, response, body) {
      if (!error && response.statusCode == 200) {
        console.log(body);
      }
    title: Node.js
    language: javascript
  - code_block: |-
      curl -X GET 'https://riddlesapidoc.vercel.app/riddles'
    title: curl
    language: bash
right_code_blocks:
  - code_block: |-
      curl -X GET 'https://riddlesapidoc.vercel.app/riddles'
    title: curl
    language: bash
  - code_block: |2-
      
        {
      "_id": "60bc3ffb5dcf8ac52f16a7fd",
      "riddle": "What has to be broken before you can use it?",
      "answer": "An egg",
      "category": "easy",
      "source": "https://parade.com/947956/parade/riddles/"
      },
      {
      "_id": "60bc3ffb5dcf8ac52f16a800",
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
