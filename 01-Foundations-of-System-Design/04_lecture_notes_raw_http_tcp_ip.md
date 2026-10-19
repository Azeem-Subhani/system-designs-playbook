Protocol:
 - In networking a protocol is a set of rules for formatting and processing data.
 - Network protocol are like common language for the computers.
 - Computers follow standart protocol to communicate.


But from a system design perspectice there are three protocols you need to know.

 - IP
 - TCP
 - HTTP

When a machiene send data to another machiene it is sent in the form of ip packet.

Think of ip packet as a fundamental unit data stored in bytes.

and it has two main components

 - ip header (it contains information about the packet such as source ip address and destination ip address and the packet size the ip version could be ipv4 and ipv6)
 - The other component is actuall data.
 - data section: The size of ip packet is limited typically about 0.065MB

 Let's say if you are sending an email if it has multiple pictures attached, it needs to be sent in multiple packets.

So when you send ip packets, you must guarentee the order in which they are sent. so that the receiver gets the data in the correct structure and take care of any lost packet.

This is where TCP comes into the play

Its pretty much built on top of the IP address.

it guarentees the two things.

 - IP packets are sent in order.
 - And IP packets are delivered to destination machiene without being damaged.
 - TCP is used in almost all web application it allow us to send long pieces of data. Which ip alone cann't do on its own.
 - To stich together all packets, each packet has tcp header in its data section.


 example: when a client machiene lets say chrome wants to connect to amazon server.

 it creates a tcp connection.

 this process of initially setting up the connection is called the handshake.

 In the handshake process the machiene sends packet to the server "Hey i want to connect with you."

 And the server machiene responds to okay you can connect.

 then the client says "ok connected".

The tcp connection can be terminated by the either of the machienes. for example you closing the browser.

The handshake takes more than a fixed amount of time the connection can timeout causing tcp connection to terminate.

TCP lacks easy to use framework, with tcp you're just sending arbitary data.

this is there http comes in.

Which introduces a higher level of abstraction on top of the tcp.

Its like the developers dont code in lower level languages like assembly language but higher level languages like java.

Developers dont write code to interact with tcp but with the http protocol.

HTTP abstraction is request response paradime and allows client server communication.

This is why modern day programming languages relies on http protocol.

There is an example of HTTP get request.

where client is requesting to server, and the server is responding back with an html file.

A simple http get request contains various parts.

include the example of get request in javascript.

Just like get request there are other types of http request like POST, PUT, DELETE, HEAD, PATCH, GET.

Often times the term REST and HTTP often use.

REST is a architecture style for distriibuted systems.

While HTTP is a network protocol for formatting and processing data.



<h2>Web Sockets</h2>

 - Protocol for bi-directional client server communication in real time.
 - That is the protocol responsible for sending and receiving data simultaneously over TCP connection.
 - In typical HTTP request the client req the data annd server responds with the data and the connection is closed.
 - Polling: polling is a standard technique used by the vast majority of the ajax applications.
 - Here's how polling works the client request the data from the server, the server calculates the response and sends back just the regular http request.
 - The client keeps sending the requst in an interval, it could be every 1 second, every 5 seconds or every 2 minutes.
 - The problem with the polling is that the client keep asking the server about the new data.
 - As a result there is a lot of new connections are made and a lot of response are the same.
 - A variation of this technique is HTTP long polling.
 - The client request the data to the server and the server doesn't respone immediately, and sometimes it refers as hanging GET. The server holds the request once the data become available. and once the data become available the server send the response.
 - Each long poll request has a timeout so the client has to connect to the server again after the timeout

 The websocket on the other hand keeps the connection open while eliminating the latency problems that arive with the long pooling.

 A websocket is a full duplex async messaging, so that the client and the server both can stream messages independantly over a tcp connection.

 the websockets was crafted to form a connection between web browser and server. it is also used in messaging apps like whatsapp.

 The websocket works in three stages.

 the client establises a appropiate webbsocket connection with a server with a websocket handshake.

 if the server supports the protocol it responds via a header to complete the handshake.

 A web socket connection is established with tcp connection. At this point both parties can start sending the data.

 Typically when a websocket is used. a wesocket handler with be connected.

 a websocket handler is a lightweight server which opens the connection with all the active users.

 so what are the applications of websockets.

  - Its heavily used in realtime web applications
  - stock trading website.
  - chat application.
  - gaming.

however a websocket will be overkill if we require data only once, or it can be quried by the simple http request. SO in this scenario better to use http instead of the websockets.
