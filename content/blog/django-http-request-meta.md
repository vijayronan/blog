
+++
title = "Django Http Request Meta"
date = 2018-06-23T14:13:16+05:30
tags = ["django","http"]
+++

A standard Python dictionary containing all available HTTP headers. Available headers depend on the client and server, but here are some examples:

```python
request.META.get('HTTP_USER_AGENT')
```

```
CONTENT_LENGTH – The length of the request body (as a string).
CONTENT_TYPE – The MIME type of the request body.
HTTP_ACCEPT – Acceptable content types for the response.
HTTP_ACCEPT_ENCODING – Acceptable encodings for the response.
HTTP_ACCEPT_LANGUAGE – Acceptable languages for the response.
HTTP_HOST – The HTTP Host header sent by the client.
HTTP_REFERER – The referring page, if any.
HTTP_USER_AGENT – The client’s user-agent string.
QUERY_STRING – The query string, as a single (unparsed) string.
REMOTE_ADDR – The IP address of the client.
REMOTE_HOST – The hostname of the client.
REMOTE_USER – The user authenticated by the Web server, if any.
REQUEST_METHOD – A string such as “GET” or “POST”.
SERVER_NAME – The hostname of the server.
SERVER_PORT – The port of the server (as a string).
```