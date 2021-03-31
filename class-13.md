# CRUD
Create | Read | Update | Delete

## Sending Form Data

### Form Architecture
Based on a client(browser) / server (web server) using HTTP protocol.

On the client side: `form` element defines how the data will be sent.
- `action`: Defines where the data should be sent. Value should be a relative/absolute url. => If missing data is sent to page containing `form`
- `method`: Defines how data is sent. Most common is GET and POST

### GET
The browser asks the server to send back a given resource. Browser sends an empty body since the body is empty. If a form is sent using GET, the 
data sent to the server is appended to the url => `www.foo.com/?say=Hi&to=Mom`

### POST
The browser uses to talk to the server when asking for a response that takes account the data provided in the body of the HTTP request. If a form is
sent using POST, the data is appended to the body of the HTTP request.
```
POST / HTTP/2.0
Host: foo.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 13

say=Hi&to=Mom
```
