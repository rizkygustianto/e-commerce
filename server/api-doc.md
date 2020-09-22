# E-Commerce CMS Server
E-Commerce CMS is an application for creating and managing an e-commerce products stock. This app has : 
* RESTful endpoint for asset's CRUD operation
* JSON formatted response

&nbsp;

## RESTful endpoints

### POST /register

> Register new user

_Request Header_
```
not needed
```

_Request Body_
```
{
    "email": "<email to be registered>",
    "password": "<password to be registered>",
    "role": "<defaults to customer in server unless specified otherwise>"
}
```

_Response (201 - Created)_
```
{
    "id": "<auto generated by db>"
    "email": "<registered email>"
    "role": "<registered role>"
    "msg": "registration successful"
}
```

_Response (400 - Bad Request)_
```
{
  "msg": "Invalid requests"
}
```
---
### POST /login

> Register new user

_Request Header_
```
not needed
```

_Request Body_
```
{
    "email": "<login credentials>",
    "password": "<login credentials>"
}
```

_Response (201 - Created)_
```
{
    "access_token": "<access_token>",
    "id": "<id number of the logged in user>"
    "email": "<email of the logged in user>"
}
```

_Response (400 - Bad Request)_
```
{
  "msg": "Invalid requests"
}
```


### GET /tasks

> Get all todo list

_Request Header_
```
{
  "access_token": "<your access token>"
}
```

_Request Body_
```
not needed
```

_Response (200)_
```
[
  {
    "id": 1,
    "name": "<product name>",
    "image_url": "<product image url>",
    "price": <product price>,
    "stock": <product stock>,
    "createdAt": "2020-09-15T10:24:16.618Z",
    "updatedAt": "2020-09-15T10:24:16.618Z"
  },
  {
    "id": 2,
    "name": "<product name>",
    "image_url": "<product image url>",
    "price": <product price>,
    "stock": <product stock>,
    "createdAt": "2020-09-15T10:24:16.618Z",
    "updatedAt": "2020-09-15T10:24:16.618Z"
  }
]
```

_Response (400 - Bad Request)_
```
{
  "msg": "Invalid request"
}
```
---
### POST /tasks

> Create new todo

_Request Header_
```
{
  "access_token": "<your access token>"
}
```

_Request Body_
```
{
    "name": "<new product title>",
    "image_url": '<new product image url>',
    "price": <new product price>,
    "stock": <new product stock>
}
```

_Response (201 - Created)_
```
{
    msg:'success adding product', 
    id: <newly created product id>
}
```

_Response (400 - Bad Request)_
```
{
  "msg": "Invalid requests"
}
```

### GET /tasks/:id

> Get a todo by ID

_Request Header_
```
{
  "access_token": "<your access token>"
}
```

_Request Body_
```
not needed
```

_Response (200)_
```
{
    "id": <product id>,
    "name": "<product name>",
    "image_url": "<product image url>",
    "price": <product price>,
    "stock": <product stock>,
    "createdAt": "2020-09-15T10:24:16.618Z",
    "updatedAt": "2020-09-15T10:24:16.618Z"
}
```

_Response (404 - Not Found)_
```
{
  "msg": "Error Not Found"
}
```
---

### PUT /tasks/:id

> Modify/Update a todo by ID

_Request Header_
```
{
  "access_token": "<your access token>"
}
```

_Request Body_
```
{
    "name": "<edited product title>",
    "image_url": '<edited product image url>',
    "price": <edited product price>,
    "stock": <edited product stock>
}
```

_Response (200)_
```
{
    [1]
}
```

_Response (400 - Bad Request)_
```
{
  "msg": "Invalid request"
}
```
_Response (404 - Not Found)_
```
{
  "msg": "Error Not Found"
}
```
---

### DELETE /todo/:id

> Delete a todo by ID

_Request Header_
```
{
  "access_token": "<your access token>"
}
```

_Request Body_
```
not needed
```

_Response (200)_
```
{
  msg: 'success deleting product'
}
```

_Response (404 - Not Found)_
```
{
  "msg": "Invalid request"
}
```

_Response (500 - Internal Server Error)_
```
{
  "msg": "Internal Server Error"
}
```
---