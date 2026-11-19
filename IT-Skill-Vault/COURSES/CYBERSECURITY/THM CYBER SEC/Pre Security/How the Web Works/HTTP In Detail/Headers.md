Headers are additional bits of data you can send to the web server when making requests.

Although no headers are strictly required when making a HTTP request, you’ll find it difficult to view a website properly.

## Common Request Headers:
﻿These are headers that are sent from the client (usually your browser) to the server.
﻿
**Host:** Tells the server **which website** you want
Ex: `Host: www.example.com
`

**User-Agent:** Identifies the **browser / device / OS and its version**
Ex:`User-Agent: Mozilla/5.0
`

**Content-Length:** Size of the request body (in bytes)
Ex:`Content-Length: 348
`

**Accept-Encoding:** tells the server **which compression formats the client can understand** for the response.
Ex:`Accept-Encoding: gzip, br, deflate
`
**Cookie:** Data sent to the server to help remember your information (see cookies task for more information).
Ex:`Cookie: key1=value1; key2=value2; key3=value3
`

## Common Response Headers

These are the headers that are returned to the client from the server after a request.

**Set-Cookie:** Stores data in the browser (sessions, login state)
Ex: `Set-Cookie: sessionid=abc123
`

**Cache-Control:** How long to store the content of the response in the browser's cache before it requests it again.  
Ex: `Cache-Control: max-age=3600
`

**Content-Type:** Type of content returned by the server
Ex:`Content-Type: text/html
`

**Content-Encoding:** It tells the server **how the request is encoded (compressed)**.
Ex: `Content-Encoding: gzip
`