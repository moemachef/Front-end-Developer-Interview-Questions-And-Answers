# Network Questions


#### What are HTTP status codes?

When client’s request to the server, server provide a HTTP (Hypertext Transfer Protocol) response status code, Which allows us to understand what is happening on the back-end of a website, determine what errors need to be fixed. All HTTP response status codes are parted into five categories.

The first digit of the status code defines the categories of response. There are five values for the first digit:

1xx (Informational): Request initiated by the browser is continuing.

2xx (Successful): The request was successfully received, understood, and processed by the server.

3xx (Redirection): Requested information that is no longer at the provided address, further action needs to be taken in order to complete the request.

4xx (Client Error): When there was a problem with the request of client.

5xx (Server Error): When client made a valid request, but the server is unable to complete the transfer.

https://medium.com/@sahelasumi/http-status-codes-31644d99fb1

#### What is the difference between HTTP protocol and TCP protocol?

HTTP = Envelope/Parcel, IP = Post Office, TCP = Delivery Truck.

One thing to bear in mind is you usually use both at the same time. Each one does a different job. The jobs they do is what primarily distinguishes them.

TCP/IP is for getting bits of data from one place to another. It's only concerned with connecting computers to each other and moving the data, not about what kind of data it is. So when you are using the web, it makes sure that the data bits coming from the server get to your machine, without errors, and in the order they were sent. It is called a "transport protocol". Think of it like a post office delivery truck.

HTTP is a kind of data packaging used by your browser, and web servers. It's not involved with delivery, just with what you have after the delivery arrives. Because it pertains to your application (program) it is called an "application protocol". Think of it as the envelope or the parcel.


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

#### What are the differences between Long-Polling, Websockets and Server-Sent Events?
#### Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
#### What are HTTP actions? List all HTTP actions that you know, and explain them.
