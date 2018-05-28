# Network Questions

#### What is the difference between HTTP protocol and TCP protocol?

1. TCP is a core operates a relatively high level; HTTP is an Application Layer protocol that is a request/response standard found in client server computing.

2. TCP provides communication services at an intermediate level between an application program and the IP; in HTTP there are a series of sessions in which the client sends a request and the server sends a reply message back to the client including the request, an error message, or another piece of information.


Read more: Difference Between TCP and HTTP | Difference Between http://www.differencebetween.net/technology/internet/difference-between-tcp-and-http/#ixzz5GoIqbxq2

https://teamtreehouse.com/community/difference-between-http-and-tcpip-protocols

#### Traditionally, why has it been better to serve site assets from multiple domains?

It's because browsers usually have limits on the number of concurrent downloads
from a domain at a moment. So, serving assets from multiple domains can
increase the concurrent level.

#### Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.

When I enter a website's URL, in the transport layer, it will ask a local DNS
what is the IP of the provided URL. We know the IP of the local DNS server by
the DHCP protocol, when a node connects to internet and gets an IP address.

After that, a browser will try to establish a TCP connection with a server
having the retrieved IP by 3-way handshake. When it establish a TCP connection,
the browser will form an HTTP request containing an HTTP header and body.

After the HTTP request is sent and the server responds with an HTTP response,
the browser will parse the HTTP response header and body, and will render the
website. If the document contains additional assets, the browser will create
HTTP requests for the assets and send them like above.

* What are the differences between Long-Polling, Websockets and Server-Sent Events?
* Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
* What are HTTP actions? List all HTTP actions that you know, and explain them.
