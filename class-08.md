# APIs

## Super Agent
a light weight progressive ajax API for flexibility, readability, and lower learning curve.

### Request Basic
A request can be initiated with the appropriate method on the `request` object such as `get` `post` `put` `delete`.  
Then calling `.then()` or `.end()` to esnd the request.
```JavaScript
 request
   .get('/search')
   .then(res => {
      // res.body, res.headers, res.status
   })
   .catch(err => {
      // err.message, err.response
   });
```
- **GET**: called by `.get()` when used with the `.query()` accepts and object. Forming a query string.
- **POST/PUT**:  sends/updates data. ==> write data
```JavaScript
  request.post('/user')
    .send({ name: 'tj', pet: 'tobi' })
    .then(callback, errorCallback)
```
- **DELETE**: uses `.del()` which deletes data.

## Regex
Used to parse/replace strings passing through data ane web scraping.

### Anchors
```
^The        matches any string that starts with The
The$        matches a string that ends with The
^The end$   exact string match (starts and ends with The end)
roar        matches any string that has the text roar in it
```

### Quantifiers
```
abc*        matches a string that has ab followed by zero or more c
abc+        matches a string that has ab followed by one or more c
abc?        matches a string that has ab followed by zero or one c
abc{2}      matches a string that has ab followed by 2 c
abc{2,}     matches a string that has ab followed by 2 or more c
abc{2,5}    matches a string that has ab followed by 2 up to 5 c
a(bc)*      matches a string that has a followed by zero or more copies of the sequence bc
a(bc){2,5}  matches a string that has a followed by 2 up to 5 copies of the sequence bc
```

### Character Classes
```
\d         matches a single character that is a digit == [0-9]
\w         matches a word character (alphanumeric character plus underscore) == [a-z0-9]
\s         matches a whitespace character (includes tabs and line breaks)
.          matches any character
```

### OR operator — | or []
```
a(b|c)     matches a string that has a followed by b or c (and captures b or c)
a[bc]      same as previous, but without capturing b or c
```

source
- https://visionmedia.github.io/superagent/
- https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285
