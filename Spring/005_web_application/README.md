<!-- HEADER -->
<div align="center">
  <h1 align="center">Web server, Web application server</h1>
</div>

# 1. Web Server
* HTTP based
* Provides the static resource
* ex) NGINX, APACHE

# 2. WAS (Web Application Server)
* HTTP based
* Provides the static resource + Web server function
* Do the application logic by executing the program code
  * Static HTML, HTTP API(JSON)
  * Servlet, JSP, Spring MVC
* ex) Tomcat, Jetty, Undertow

# 3.1 Web System Package - WAS, DB
* WAS takes too much part, may have the server overload
* It may hard to execute because the most expensive application logic is the static resource
* WAS error - not possible to expose the error screen

> Structure
```shell
Client
v
WAS - HTML, CSS, JS / Image / Application logic
v
DB
```

# 3.2 Web System Package - WEB, WAS, DB
* Web server executes the static resource
* Web server grants the request to WAS if application logic is required
* WAS does the important application logic
* Pros: efficient resource management
* When error in WAS or DB, WEB server can provide the error screen

> Structure
```shell
Client
v
Web Server - HTML, CSS, JS / Image
v
WAS - Application logic
v
DB
```
