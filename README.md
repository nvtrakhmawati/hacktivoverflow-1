# hacktivoverflow

## Basic Route

### Register New User

- Method
    - **POST**
- Route
    - `/register`
- Body
    ```JS
    {
        name: "<String>",
        email: "<String>",
        password: "<String>"
    }
    ```
- Response
    - `code: 201`
    ```JS
    {
        _id: "<ObjectId>",
        name: "<name>",
        email: "<email>",
        password: "<hashed password>",
        watch_tag: []
    }
    ```
### Login

- Method
    - **POST**
- Route
    - `/login`
- Body
    ```JS
    {
        email: "<String>",
        password: "<String>"
    }
    ```
- Response
    - `code: 200`
    ```JS
    {
        accesstoken: "<generated access token>",
        watch_tag: "<Array of String>"
    }
    ```
### Get User Watch Tag

- Method
    - **GET**
- Route
    - `/tag`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Response
    - `code: 200`
    ```JS
    {
        watch_tag: "<Array of String>"
    }

### Update User Watch Tag

- Method
    - **PATCH**
- Route
    - `/`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Body
    ```JS
    {
        watch_tag: "<Array of String>",
    }
    ```
- Response
    - `code: 200`
    ```JS
    {
        watch_tag: "<Array of String>"
    }

___

## Question Route

### Get All Question

- Method
    - **GET**
- Route
    - `/questions`
- Response
    - `code: 201`
    ```JS
    [
        {
            "upvotes": "<Array of User ObjectId>",
            "downvotes": "<Array of User ObjectId>",
            "answers": "<Array of Answer ObjectId>",
            "tags": "<Array of String>",
            "_id": "<ObjectId>",
            "title": "<String>",
            "content": "<String>",
            "owner": "<Object User>",
            "created_at": "<timestamp>",
            "updated_at": "<timestamp>",
            "__v": 0
        },
        { "<Object Question>" }, ...
    ]
    ```
### Get One Question

- Method
    - **GET**
- Route
    - `/questions/:id`
- Response
    - `code: 200`
    ```JS
    {
        "upvotes": "<Array of User ObjectId>",
        "downvotes": "<Array of User ObjectId>",
        "answers": "<Array of Answer ObjectId>",
        "tags": "<Array of String>",
        "_id": "<ObjectId>",
        "title": "<String>",
        "content": "<String>",
        "owner": "<Object User>",
        "created_at": "<timestamp>",
        "updated_at": "<timestamp>",
        "__v": 0
    }
    ```

### Create New Question

- Method
    - **POST**
- Route
    - `/questions`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Body
    ```JS
    {
        title: "<String>",
        content: "<String>",
        tags: ["<String>", "<String>", ...]
    }
    ```
- Response
    - `code: 201`
    ```JS
    {
        "upvotes": [],
        "downvotes": [],
        "answers": [],
        "tags": [
            "<String>",
            "<String>",
            ...
        ],
        "_id": "<ObjectId>",
        "title": "<String>",
        "content": "<String>",
        "owner": "<ObjectId>",
        "created_at": "<timestamp>",
        "updated_at": "<timestamp>"
    }
    ```

### Update Question

- Method
    - **PATCH**
- Route
    - `/questions/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Body
    ```JS
    {
        title: "<String>",
        content: "<String>",
        tags: ["<String>", "<String>", ...]
    }
    ```
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        nModified: 1,
        ok: 1
    }
    ```
### Upvote Question

- Method
    - **PATCH**
- Route
    - `/questions/upvote/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        nModified: 1,
        ok: 1
    }
    ```

### Downvote Question

- Method
    - **DELETE**
- Route
    - `/questions/downvote/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        nModified: 1,
        ok: 1
    }
    ```

### Delete Question

- Method
    - **DELETE**
- Route
    - `/questions/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        deletedCount: 1,
        ok: 1
    }
    ```

---

## Answer Route

### Create Answer

- Method
    - **POST**
- Route
    - `/answers/:questionId`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Body
    ```JS
    {
        content: "<String>"
    }
    ```
- Response
    - `code: 201`
    ```JS
    {
        "upvotes": [],
        "downvotes": [],
        "_id": "<ObjectId>",
        "content": "<String>",
        "owner": "<ObjectId>",
        "created_at": "<timestamp>",
        "updated_at": "<timestamp>"
    }
    ```
### Update answer

- Method
    - **PATCH**
- Route
    - `/answers/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Body
    ```JS
    {
        title: "<String>",
        content: "<String>",
        tags: ["<String>", "<String>", ...]
    }
    ```
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        nModified: 1,
        ok: 1
    }
    ```
### Upvote answer

- Method
    - **PATCH**
- Route
    - `/answers/upvote/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        nModified: 1,
        ok: 1
    }
    ```

### Downvote answer

- Method
    - **DELETE**
- Route
    - `/answers/downvote/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        nModified: 1,
        ok: 1
    }
    ```
    
### Delete answer

- Method
    - **DELETE**
- Route
    - `/answers/:id`
- Header
    - `{ accesstoken: "<generated access token>"}`
- Response
    - `code: 200`
    ```JS
    {
        n: 1,
        deletedCount: 1,
        ok: 1
    }
    ```

---

## Usage

Run this command: 

Server:
```
$ npm install
$ npm run dev
```
Client:
 
```
$ npm install
$ npm run serve
```

## Access point:
Server: http://localhost:3000

Client: http://localhost:8080