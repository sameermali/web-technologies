# web-technologies
common repo for web technologies like docker, kubernetes etc.

## technologies
- [docker](https://github.com/sameermali/web-technologies/docker/docker.md)


## web application
- authentication: deals with user validation.  
  is user valid ?
- authorization: deals wih user access validation to certain resource.   
  does user have right to access particular resource. 
- HTTP/Browser cookie
  - types based on expiry
    - session cookie  : expires if browser closed
    - permanent cookie: expires at specific time (Expires) or after specific length of time (Max-Age)
  - types
    - secure cookie  : sent only over HTTPS
    - HttpOnly cookie: inaccessible to javascript's document.cookie api
  - Set-Cookie: HTTP response header sends cookie from server to user agent
  - scope
    - domain: allowed hosts. if specified sub domain also considered.
    - path: url that must be present in requested URL to send cookie.
- proxy
  - forward proxy: acting on behalf of requestor  
    (client <--> proxy) <--> server  
    client knows all 3 machines
  - reverse proxy: acting on behalf of service/content provider
    client <--> (proxy <--> server)
    client only knows about proxy
