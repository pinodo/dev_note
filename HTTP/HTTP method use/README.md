<!-- HEADER -->
<div align="center">
  <h1 align="center">HTTP Method Use</h1>
</div>

# 1. Data transportation from Client to the Server

## 1.1 Data transportation through query parameter
* GET
* Sort filter (search keyword)

## 1.2 Data transportation through message body
* POST, PUT, PATCH
* Register, Order products, Register the resource, Change the resource

## 1.3 Examples

### 1.3.1 Search the static data
> Image, Static text document
```shell
(1) Request - not using a query parameter
GET /static/image1.jpg HTTP/1.1
Host: localhost:8080

(2) Response
HTTP/1.1 200 OK
Content-Type: image/jpeg
Content-Length: 35820

iaidnl1294 ... kdlfknlls
```

### 1.3.2 Search the dynamic data
> Search, Sort filter on the bulletin list
```shell
(1) Request - using a query parameter
GET /search?q=hello&hl=ko HTTP/1.1
Host: www.google.com

(2) Response - based on the query parameter, the server sorts, filters, then creates the result dynamically
```

### 1.3.3 Data transportation through HTML Form
> Register, Order products, Change the data
```shell
[Form data]

** POST **
(1) Web form
username: {username}
age: {age}
[submit btn]
<form action="/save" method="post">
  <input type="text" name="username" />
  <input type="text" name="age" />
  <button type="submit">Submit</button>
</form>

(2) Request
POST /save HTTP/1.1
Host: localhost:8080
Content-Type: application/x-www-form-urlencoded

username={username}&age={age}

** GET **
(1) Web form
username: {username}
age: {age}
[submit btn]
<form action="/save" method="get">
  <input type="text" name="username" />
  <input type="text" name="age" />
  <button type="submit">Submit</button>
</form>

(2) Request
POST /customers?username={username}&age={age} HTTP/1.1
Host: localhost:8080
```
```shell
[Multipart form data]

(1) Web form with an uploaded file
username: {username}
age: {age}
file: [select file btn] image1.png
[submit btn]
<form action="/save" method="post" encrypt="multipart/form-data">
  <input type="text" name="username" />
  <input type="text" name="age" />
  <input type="file" name="file1" />
  <button type="submit">Submit</button>
</form>

(2) Request
POST /save HTTP/1.1
Host: localhost:8080
Content-Type: multipart/form-data; boundary=-----XXX
Content-Length: 10457
------XXX
Content-Disposition: form-data; name="username"
kim
------XXX
Content-Disposition: form-data; name="age"
20
------XXX
Content-Disposition: form-data; name="file1"; filename="image1.png"
Content-Type: image/png
109390skanlkdfjg9032klsdiogna02...
------XXX--
```

### 1.3.4 HTML Form data transportation Summary
* HTML Form submit: POST
  * ex) register, order, modify the data
* Content-Type: application/x-www-form-urlencoded
  * Transport the content of the form through the message body (kdy=value, query parameter format)
  * process the transportation data by url encoding - ex) abc !: abc%20%21
* HTML Form: can also transport w/ GET method
* Content-Type: multipart/form-data
  * Used when transporting the binary data such as file upload
  * Transport form content plus other types of files
* HTML Form: GET or POST

### 1.3.5 Data transportation through HTTP API
> Register, Order products, Change the data
> 
> Server to Server, App client, Web client (Ajax)
```shell
(1) Request
POST /customers HTTP/1.1
Content-Type: application/json

{
"username": "unanimous",
"age": 19
}

(2) Server
/customers
```
* Server to Server
  * Backend system transportation
* App client
  * Iphone, Android
* Web client
  * Transportation through JavaScript(AJAX) instead of HTML Form transportation
  * ex) Web client and API transportation like in React, VueJS
* POST, PUT, PATCH: data transportation through the message body
* GET: search, transport data with query parameter
* Content-Type: application/json
  * ex) TEXT, XML, JSON, etc,.

# 2. Structure HTTP API

## 2.1 HTTP API - Collection
> POST register - ex) Provides the managing customers API
```shell
Customer list     /customers      => GET
Customer register /customers      => POST
Customer search   /customers/{id} => GET
Customer modify   /customers/{id} => PATCH, PUT, POST
Customer delete   /customers/{id} => DELETE
```
---
* Client doesn't know about the newly registered resource's URI
* Server creates the resource URI to the newly created one
  ```
  HTTP/1.1 201 Created
  Location: /customers/123
  ```
* Collection
  * Resource directory managed by server
  * Server creates and manages the resource URI
  * Collection: /customers

## 2.2 HTTP API - Store
> PUT register - ex) Manages the static contents, Manage the remote file 
```shell
File list                 /files            => GET
File search               /files/{filename} => GET
File register             /files/{filename} => PUT
File delete               /files/{filename} => DELETE
File register(a bunch of) /files            => POST
```
---
* Client should know the resource URI
  * File register /files/{filename} => PUT
  * PUT /files/abc.jpg
* Client designates the resource URI
* Store
  * Resource repository managed by client
  * Client knows and manages the resource URI
  * Store: /files

## 2.3 HTML FORM
> Manages web page customers
> 
> Only GET or POST
> 
> Resolve the problem by using AJAX
```shell
Customer list           /customers                            => GET
Customer register form  /customers/new                        => GET
Customer register       /customers/new, /customers            => POST
Customer search         /customers/{id}                       => GET
Customer modify form    /customers/{id}/edit                  => GET
Customer modify         /customers/{id}/edit, /customers/{id} => POST
Customer delete         /customers/{id}/delete                => POST
```
* HTML FORM: only supports GET, POST
* Control URI
  * To resolve the restriction, control URI uses the resource path as a verb form
  * /new, /edit, /delete