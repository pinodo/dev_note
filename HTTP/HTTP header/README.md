<!-- HEADER -->
<div align="center">
  <h1 align="center">HTTP header</h1>
</div>

## 1. HTTP header
```shell
header-field = field-name ":" OWS field-value OWS (OWS: allow space)

GET /search?q=hello&hl=ko HTTP/1.1
Host: www.google.com >>> HEADER

HTTP/1.1 200 OK
Content-Type: text/html;charset=UTF-8 >>> HEADER
Content-Length: 3423

<html>
  <body>...</body>
</html>
```

### 1.1 Usage
* All additional information that is required in HTTP transportation
* ex) Message body content, Size of message body, Zip, Auth, Request client, Server info, ...

### 1.2 Types
* General header: Information that applies to the overall message
  * ex) Connection: close
* Request header: Request info
  * ex) User-Agent: Mozilla/5.0 (Macintosh; ..)
* Response header: Response info
  * ex) Server: Apache
* Entity header: Entity body info
  * ex) Content-Type: text/html, Content-Length: 3521

### 1.3 HTTP standard
* In 1999, RFC2616
* In 2014, RFC7230~7235

#### 1.3.1 RFC723x changes
* Entity -> Representation
* Representation = representation Metadata + representation Data

### 1.4 HTTP body
* Transports representation data thru message body
* Message body = payload
* Representation header provides the info that translates the representation data
  * Such as data type(html, json), data length, zip info, etc.

## 2. Representation
* Content-Type
* Content-Encoding
* Content-Language
* Content-Length

### 2.1 Content-Type
* Media type, Literal encoding
* ex)
  * text/html; charset=utf-8
  * application/json
  * image/png

### 2.2 Content-Encoding
* To zip the representation data
* Zip at the location where sending the data, then add the encoding header
* Unzip at the location where reading the data with the information of the encoding header
* ex)
  * gzip
  * deflate
  * identity

### 2.3 Content-Language
* Represents the natural language of representation data
* ex)
  * ko
  * en
  * en-US

### 2.4 Content-Length
* Byte unit
