<!-- HEADER -->
<div align="center">
  <h1 align="center">URI Web Browser</h1>
</div>

# URI (Uniform Resource Identifier)

## URI - URL(Locator) / URN(Name)

```
[schema]://[userinfo@]host[:port][/path][?query][#fragment]
foo://example.com:8042/over/there?name=alvin#nose

schema (foo)
 
authority (example.com:8042) --> DNS search
 
path (/over/there)
 
query (?name=alvin)
 
fragment (#nose)
```

```
1. Web Browser sends a TCP/IP packet to the server
2. The server unpacks the packet, read and interpret
3. The server sends a HTTP response message
```