The polling is when a client req to a server a piece of data that it want on a recurrence basis. (every x seconds.)

IN contrass the streaming is when a server pushes data to the client without any request from the client.

In chat application you can use polling, but lets say you wait 30 seconds to poll, but the client has to wait 30 seconds to see new messages appear on the screen. but instead of 30 seconds you can reducde the time but the issue with that is a lot of load on the server.

In streaming instead of client repeatedly requesting data from the server, you gonna have your client open a long lived connection with your server, typically its done what we call is socket.
A socket is a file that lives on your computer, where your computer can read to write to to communicate with the server.
In pooling the client req for data, but in streaming the client says hey server im listening for the data, and the server sends the data.

<h2>Caching</h2>
Caching is basically storing the data to a different location than the original location so that it can be retreived faster.

Lets say we have a client that interact with the server that interact with the database.

 - you can cache at the client level so that client doesn't have to request data again and again to the server.
 - you can cache at the server level, so that the server will call the database at once and cache the data at the server level.
 - Instead of caching at the client and server level you can cache the data between server and database.
 - you can have the caching even at the hardware level.


 What are the common use cases when the caching is helpful.

 the client req to server.
 The server query database.
 Database return result to server.
 The server return data to client.

 by caching the result of network calls, you can speed up the operation.

 The client request data to the server and if it has cached data then it doesn't have to query database it can send client the data right away.

computationally expensive.
 - you are not saving a network call but you are saving an operation which takes long time to procees from a server.

 The main goal of caching is to speed up the system.

 Lets say there are millions of user that want to access the profile of a celebrity (lets say on instagram)

 there would be many client, or could be many servers. to the server wont req database every single time the client request the profile of this celebrity.

 the servers may have 1 cache system or even each server may have its own cache.

  - reduce network calls
  - computationally expensive
  - prevent data hotspots

So far we only saw the example of caching where data need to be read. not the data that need to be write.  


lets take an example of social app like facebook or twitter, 

 - where user can read write or edit their post.

We have a client which is writing a post, and then post are sent to the server and server is saving data to the database.

Now if you want to cache those posts that is on the server level in memory, you now have two sources of truth, (in memory and database)

so how you deal with these two sources of truths,

how we can tell do we write to the cache or we write to the database or we do it at the same time?

we have two popular caching system.

 - write through cache
 - write back cache

write through cache, when to edit the data the system will write through the both source of truth at the same time. (the cache and the database)

If a user request to the server the server firrst will overwrite it in the cache then it will update the database.

now the data will always be in sync.

the downside of this is that, now you'll always has to go to the database so you are not able to minimise the network calls here.

which brings us to second type of popular cache.

 0 the write back cache

 Now if the user wants to edit their post, the server will update the cache and immediately send the response back to the client without touching the database.

 now your database is out of sync, however behind the scenes, the system will update the database async
 which can be done in different ways may be randomly or on a scheduled basis

 when user req to update the post we only update the cache but behind the scenes we update the database async.

<h2>Hasing</h2>

 In its simplest form, hasing is the proces of converting arbitary piece of data in a fixed sized values typically an integer value.

 the data can be a user name, ip address or anything that can be hashed into the integer value.  

 To understand the hasing lets understand the load balancer which used to distribute network traffic across servers.

 here we have three clients c1 c2 c3

 there are three servers that clients can talk to A B and C.

 So instead of client talking to the server directly we have a load balancer in between. So that client request the routed evenly distributed across servers.

 When a load balancer route or redirects a request from client to a server. It needs to have a server selection strategy.

 that is which request will be servered by which server.

 1 approach would be randomly selecting the server.
 2 approach would be round robin. (the load balancer go to each server in a specific order)

 however depending upon the nature of the traffic the strategy could be problematic


 lets say if a req go to client to load balancer then to a server and it takes a long time to process, its a computationally expensive request. and one way to deal with the request is caching.

 so if a load balancer is following randomly or round robin selection, there could be unnessary cache misses. 

 so we need to have a better strategy so that same request goes to same server to avoid unnessary expensive computation.

 This is one of the places here hashing can be useful.

 when a request goes to the load balancer so because of the hash value we can route the request to the correct server.

 let's say we have a hasing in place which takes the name of thee each client and transform it to an integer value 

 c1 after hasing is 11 and c2 after hasing is 12 and c3 after hasing is 13.

 the strategy is modulus % (number of server)

 11 % 3 = 2
 12 % 3 = 0
 13 % 3 = 1

 so all request from c1 will go to C server
 so all request from c2 will go to A server.
 so all request from c3 will fo to B server.


 maximising the cache hits and minimising the expensive computation.

 user dont write their own hasing functions, they used industry wide hasing functions like
  - MD5
  - SHA-1
  - Bcrypt
