<!-- HEADER -->
<div align="center">
  <h1 align="center">HTTP Status</h1>
</div>

# 1. Introduction

## 1.1 Status Code
> The server notifies the process status as a response from the request from client

* 100th (Informational): Request send, processing
* 200th (Successful): Proceed, normal status
* 300th (Redirection): Additional action is needed to complete the request
* 400th (Client Error): Wrong grammar, etc,. Server cannot process the request
* 500th (Server Error): Server cannot process the request

### 1.1.1 100th
```shell
Hardly used in a real world
```

### 1.1.2 200th
* 200 OK            - Successful request
* 201 Created       - Successful request, made a new resource
* 202 Accepted      - Request sent, but not proceed
* 204 No Content    - Server successfully completed the request, but no data for the response payload body

### 1.1.3 300th: Redirection
> Web browser automatically redirect to Location if the result of 300th response has Location header
```shell
Redirct Flow

(1) Request
GET /event HTTP/1.1
Host: localhost:8080

(2) Response
HTTP/1.1 301 Moved Permanently
Location: /new-event

(3) Auto Redirect

(4) Request
GET /new-event HTTP/1.1
Host: localhost:8080

(5) Response
HTTP/1.1 200 OK
...
```
```shell
Redirect Types

(1) Permanent Redirection: URI of specific resource has moved
  ex) /customers -> /users
  ex) /event -> /new-event

(2) Temporary Redirection: temporal modification
  => After order is completed, redirect to order result
  => Post/Redirect/Get

(3) Special Redirection
  => Use cache instead of the result
```

#### 1.1.3.1 Permanent Redirection
* 301 / 308
* URI of the resource is modified permanently
* Search engine detects the modification
```shell
301 Moved Permanently
=> Request method is changed to GET when redirecting
=> It may removes the body

308 Permanent Redirect
=> Same as 301
=> Maintain the request method and the body
  - when request used the POST and when there's a message in the body
```

#### 1.1.3.2 Temporary Redirection
* 302 / 307 / 303
* URI of the resource is modified temporarily
* You should not change URI in the search engine
```shell
302 Found
=> Request method is changed to GET when redirecting
=> It may removes the body

307 Temporary Redirect
=> Same as 302
=> Maintain the request method and the body
  - You must not change the request method

303 See Other
=> Same as 302
=> The request method changes to GET
```
```shell
Example (Before)

** URI: /order **
(1) Request
POST /order HTTP/1.1
Host: localhost:8080

itemId=pen&count=1

(2) Save order data to DB

(3) Response
HTTP/1.1 200 OK

<html>Order is completed</html>

** URI: /order **
(4) Refresh on the result page
POST /order HTTP/1.1
Host: localhost:8080

itemId=pen&count=1

(5) Save order data to DB

(7) Response
HTTP/1.1 200 OK

<html>Order is completed</html>
```
```shell
Example (After)

** URI: /order **
(1) Request
POST /order HTTP/1.1
Host: localhost:8080

itemId=pen&count=1

(2) Save order data to DB

(3) Response
HTTP/1.1 302 Found
Location: /order-result/77

(4) Auto redirect
** URI: /order-result/77

(5) Request
POST /order-result/77 HTTP/1.1
Host: localhost:8080

(6) Search order data 77th

(7) Response
HTTP/1.1 200 OK

<html>Order is completed</html>

(8) Refresh on the result screen
GET /order-result/77
Request only for the result screen (moves forward to (5))
```

#### 1.1.3.3 Special Redirection
* 300 / 304
```shell
300 Multiple Choices
=> Not used

304 Not Modified
=> Used for cache
=> It tells client that the resource is not modified, so client reuses the stored cache in the local PC
=> 304 response should not contains the message body since it has to use local cache
=> When conditional GET, HEAD is requestd, it uses 304
```

### 1.1.4 400th: Client Error
* Upon request, since there's a grammar error or etc, server cannot process the request

#### 1.1.4.1 400 Bad Request
* Request phrase, message
* Client should revise the request content and resend them
* ex) A wrong request parameter, API spec doesn't match

#### 1.1.4.2 401 Unauthorized
* Not authenticated
* Authentication: checks who is me
* Authorization: grants authority (Authentication before Authorization)

#### 1.1.4.3 403 Forbidden
* ex) Logged in as a user who is not an admin, and tries to access to the admin-level resource

#### 1.1.4.4 404 Not Found
* Request resource is not in the server 

### 1.1.5 500th: Server Error
* Server internal error

#### 1.1.5.1 503 Service Unavailable
* A temporary overload in the server.
* By sending a Retry-After header field, it is possible to seek how many times will be taken until restoration.
