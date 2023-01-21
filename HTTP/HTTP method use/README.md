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
```
```shell
[Multi data]

(1) Web form with the uploaded file
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

### 1.3.4 Data transportation through HTTP API
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
```