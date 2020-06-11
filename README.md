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

## ulimit
- ulimit provides control over resources available to each user via a shell
```
ulimit -a  \\ display all settings
```
- hard limit vs soft limit  
  - **hard limit** is the maximum allowed to a user, set by the superuser/root. This value is set in the file /etc/security/limits.conf. Think of it as an upper bound or ceiling or roof.
  - **soft limit** is the effective value right now for that user. The user can increase the soft limit on their own in times of needing more resources, but cannot set the soft limit higher than the hard limit.
- in linux `ulimit -u` shows max user processes which is actually threads   
https://unix.stackexchange.com/questions/322056/does-nproc-in-limits-conf-refers-to-number-of-processes-or-number-of-threads
- exceeding soft limit (usually 1024) i.e. threads are more than 1024 may result in `OutOfMemoryError: Unable to create new native thread` in java application  