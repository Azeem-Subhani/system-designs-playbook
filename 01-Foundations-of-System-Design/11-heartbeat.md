HeartBeat

Just like your heart beats to show you are alive.

servers sends heart beat to show they are alive too.

heartbeat or healthcheck are often used interchangebly.

technically a heartbeat is just a signal 1 an alive signal

Imagine you have bunch of servers running together how do they know if the other servers are still working.

how do they know if 1 of them has crashed.

thats excatly what heartbeat solves.

its basically servers saying to each other,

hey i am still here hey i am still here hey i am still here.

at regular intervals.


A heartbeat just a periodic signal saying "I'm alive and functioning normally."


lets say you have server a and server b every 5 seconds they send messsage to each other hey i am good.


lets say server b doesn't receive the heartbeat for 5 seconds.

then 5 seconds pass. then more 5 seconds

then serve check i should have received 3 heart beats by now. 

so server b assumes that serevr a is down.


we dont assume faileure after 1 heart beat. you know networks cann be flaky.


but if you miss multiple heartbeats in a row. something is definately wrong.

so the heartbeat helps us with two major things 1 routing decisions.

routing decisions: figuring out which serevrs can handle new requests.

failure detection: knowing when something goes down so we can response appropriately.


let me walk you through different approaches.

you'll se each approach has a trade off.

 - 1: push based heartbeat
 - 2: pull based heartbeat
 - 3: with acknowledgement 
 - 4: with quorum

 push based: The server proactively send heartbeats. fast detection, high overhead (the server keeps telling everything hey i am alive) (its good for the systems where you need to know about the failure as quickly as possible.)

 pull based: Also called pooling, instead of server shouting hey i am alive, you have 1 center monitor that ask priodically every server. the server onnly answers when its asked. but the trade of is failure detection is slow.


Here is another variation

with acknowledgement based heart beat:
 - the server a send heartbeat to server b, the server b has to send an acknowledgement yep i got your message."
It validates two things, it confirm server a is alive, number 2 it confirms that communication channel works between these servers. the downside is you doubleing your network traffic.



 with quorum based heartbeats: a server isn't considered alive until or unless a majority of other servers confirms, its alive.

 let's say you have  5 servers, and the server a send the heartbeath to all other 5 servers. if 3 of them see server A then the server A is considered alive. This is really small it protects against false positives.

 network overhead is significant, reduces false positive. you use it in critical systems where you cannot make the wrong decision.



how often should server sent heartbeat?

too frequest: (1 - 2 sec) the failures will be detected too fast.
too slow: (3 min delay) - now the network is quiter, but it will take 3 minutes to detect a down server.
sweet spot: for the most of the web services: something like 5 to 10 seconds works really well


there are many other patterens like

 - ping based heart beat: servers ping each other.
 - gossip protocol: instead of talking everyone, the servers share heart beat with their neibors
 - leader-based: leader election: one designated leader collects data from all other servers. giving it a centralize view of a system health.
