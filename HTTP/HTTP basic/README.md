<!-- HEADER -->
<div align="center">
  <h1 align="center">HTTP basic</h1>
</div>

# What is HTTP?
> HTTP - HyperText Transfer Protocol
> 
> Transport everything in a message
> 
> * HTML, TEXT
> 
> * IMAGE, VOICE, VIDEO, FILE
> 
> * JSON, XML
> 
> * When transporting btw servers, mostly uses HTTP

> HTTP/0.9 - 1991
> 
> HTTP/1.0 - 1996
> 
> HTTP/1.1 - 1997: Mostly use this
> 
> HTTP/2 - 2015: Improved functionality
> 
> HTTP/3 - ongoing: Using UDP instead of TCP

> TCP: HTTP/1.1, HTTP/2
> 
> UDP: HTTP/3

## HTTP Features
1. Client-Server structure
2. Stateless Protocol, Connectionless
3. HTTP message
4. Simple, Scalable

### 1. Client-Server structure
```
> Request Response
> Client requests to the server
> Server makes a result of the request, then response
```

### 2.1 Stateless protocol
```
> Server does not preserve the client's state
> Pros: Server scale out
> Cons: Client transports the additional data
```
```
Example

<Stateful>
cust: How much is this laptop?
merchA: It costs $1000

cust: I'll buy two of them
merchB: ? What will you going to buy?

cust: I'll go for debit
merchC: ? What, how many will you going to buy? And credit or debit?

<Stateless>
cust: How much is this laptop?
merchA: It costs $1000

cust: I'll buy two laptops
merchB: It costs $2000. Credit or debit?

cust: I'll buy two laptops and debit please.
merchC: Charged $2000
```
```
Stateful: Login / browser cookie, server session are used
Stateless: A simple service introduction screen
```

### 2.2 Connectionless
```
> HTTP uses a connectionless model
> Response rate <= 1 second
> Even if a thousand of people use the service about a hour, the server actually deals with less than a ten of requests
> Efficient  
```
```
Limitation - Need to make a new TCP/IP connection -> Additional 3-way handshake time occurs
Solution - HTTP persistent connections
```

### 3. HTTP message
```
<HTTP Request message>

GET /search?q=hello&hl=ko HTTP/1.1  === start-line
Host: www.google.com                === header
                                    === empty line (CRLF)

<HTTP Response message>
HTTP/1.1 200 OK                         === start-line
Content-Type: text/html;charset=UTF-8   === header
Content-Length: 3528                    == 
                                        === empty line (CRLF)
<html>                                  === message body
  <body>...</body>                      ==
</html>                                 ==
```
```
HTTP-message = start-line
               *( header-field CRLF ) 
               CRLF
               [ message-body ]
```
```
<HTTP header>

header-field = field-name ":" OWS field-value OWS (OWS: allow to use the empty space)
> All the additional information that are required when HTTP transportation
> Examples: body message, messege body size, compression, auth, requested info, server application info, cache administration info, ...
```