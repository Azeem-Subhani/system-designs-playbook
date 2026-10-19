Latency & Throughput.

If you ever played an online game, ever feel lag, that is high latency and low throughput.

latency and throughput are the two important performance metric for the software system.

They are simple concepts but people mix them up all the time, even in the technical interviews.

latency: 
 - its a measure of delay
 - "How long does it take for data to travel from one point in the system to another"

Network latency
 - How long for a request it will take from the client which is your lapptop to the server.

 when you type google.com in the browser and hit enter

 The time between pressing the enter and you seeing the google home page, thats network latency.

 Then there is disk latency and Memory latency.

 how long it will take to read or write data from your hard drive ssd or ram.


 Now different systems have different latency requirements.

  - Online Video games need exteremly low latency (event if a 100ms delay when you press a button and when your character moves, the game feels unplayable)
  - Video Calls are the same, high latency means awkward pauses and people talking each of them.
  - High Frequency Trading system can't tolorate even for a few extra mili seconds.


But there are other systems that can tolorate high latency

 - For example air line booking system and banking systems leans toward the consistant and correctnace over the latency, its ok for a transaction to take some extra seconds as long as we dont double charge

 In the system design interviews always ask
  - how latency sensitive in this system?


  Throughput:
   - it measure capacity
   - "How much work can the system handle in a given time"

In networking throughput is measure in megabits per seconds or gigabits per seconds.

your home internet might have 100mbps, thats how much data your ISP can transfer to you every second.

for web servers the throughput is measured in request per seconds.

if your server can handle 1000 requests per seconds, thats your through put.

and 100000 people request your server at a given seconds, the system becomes slow and request are queing and slow responses, that low throughput.


How do you increase the throughput when your server is overwhelmed.

first there is vertical scaling, it means upgrading your server, add more CPU add more RAM, and add faster disk. So server can handle more requests per seconds.
The downside? There is a limit you can keep adding resources to machiene forever.

and thats why the horizontal scaling is the more preferred approach.

 - it means adding more servers to your system
 - instead of 1 most powerful super system, you distribute the load accross multiple servers using load balancer.
 - you can handle more requests simultaneously, with more machienes working in parallel.
 - Thats the better long term strategy. Google and Netflix uses 10000s of servers working together.

Latency and throughput are not the same.
you can have
 - low latency and high through put
 - low latency and low throughput
 - high latency and low throughput
 - high latency and low throughput

 Every System has trade ofs.
 if you want low latency use cashing to keep data in memory but the cache has limited size which can affect throughput
 if you want high throughput batch requests together and process them at once. but batching introduce delays increasing latency.

 so in interview always discuss the trade offs show that there is no one size that fits all however it depends on your requirements.
