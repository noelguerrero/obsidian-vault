When we access a website, your browser will need to make requests to a web server for assets such as HTML, Images, and download the responses. Before that, you need to tell the browser specifically how and where to access these resources, this is where URLs will help.


## URL (Uniform Resource Locator)
It is an instruction or the address on how to access a resource on the internet.
![[Pasted image 20260116110642.png]]

- **Scheme:** It tells the browser what protocol you used (HTTP, HTTPS, FTP (File Transfer Protocol)).
- **User:** It is used for authentication but not it is too risky to put into URL.
- **Host:** The domain name or the address of the website.
- **Port:** Tells which **service port** to use (HTTP -> 80, HTTPS -> 443).
- **Path:** File location or the resource that are trying to access.
- **Query String:** Sent an extra bits for data to request the specific file or information.
- **Fragment:** It points the specific section of a page.

## Making a Request
It's possible to make a request to a web server with just one line **GET / HTTP/1.1**

![[Pasted image 20260116111847.png]]

But for a much richer web experience, you’ll need to send other data as well. This other data is sent in what is called headers, where headers contain extra information to give to the web server you’re communicating with, but we’ll go more into this in the Header task.

**Example Request:**
```http
GET / HTTP/1.1

Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/
```
**Line 1:** This request is sending the GET method ( more on this in the HTTP Methods task ), request the home page with / and telling the web server we are using HTTP protocol version 1.1.

**Line 2:** We tell the web server we want the website tryhackme.com

**Line 3:** We tell the web server we are using the Firefox version 87 Browser

**Line 4:** We are telling the web server that the web page that referred us to this one is `https://tryhackme.com`.

**Line 5:** HTTP requests always end with a blank line to inform the web server that the request has finished.

**Example Response:**
```http
HTTP/1.1 200 OK

Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98


<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>
```

**Line 1:** HTTP 1.1 is the version of the HTTP protocol the server is using and then followed by the HTTP Status Code in this case "200 OK" which tells us the request has completed successfully.

**Line 2:** This tells us the web server software and version number.

**Line 3:** The current date, time and timezone of the web server.

**Line 4:** The Content-Type header tells the client what sort of information is going to be sent, such as HTML, images, videos, pdf, XML.

**Line 5:** Content-Length tells the client how long the response is, this way we can confirm no data is missing.

**Line 6:** HTTP response contains a blank line to confirm the end of the HTTP response.

**Lines 7-14:** The information that has been requested, in this instance the homepage.