Single point of failure SPOF

A single point of failurem can bring down an entire system if it fails.

if one server creash, one network link or 1 database outage, takes everything offline. thats the single point of failure.

the main goal is identify and take them down, before they take down the whole system.


A simple arhitecture.

The client request -> the requests hit AWS API gateway (a receptionist at the frontdesk it checks who you are, figure out where you go and send you to the right place) -> The gateway passes the request to the load balancer (its like the traffic controller, its job is to distibute request acceoss servers so no single server gets overwhelmed) -> application servers (in aws terms these runs on something EC2 instances(but really there are virtual computers living in the cloud)) -> Application server talks to the database.

In the above system you api gateway, load bbalancer and servers and database all sitting on the availability zone.

Think of an availability zone as a single data center building.

AWS organizes things by regions, like es-east-1 in the north virginia, each region has multiple data center building called availability zones for backup purposes.

Look closer the above arhitecture hides several cirital weaknesses.

Number 1: API gateway, see that there is only 1 api gateway if it creashes there is no way to reach the app. think of it like a store with only 1 door which is broken.

Then there are application servers app server 1 and app server 2, notice where they are location they are located in the same availability zone, lets say there is a power outage, network failure the whole data center goes down.

Then there is a database, this is mostly the bigger point of failure in any system. if you are using 1 database, every read every write depends on 1 database.

If the traffic going through 1 load balancer, if that fails everything behind it becomes unreachable.

Here what most of the people misses, if the whole infra is sitting in 1 data-center i.e. availability zone, you are still vulnurable

how do we fix this.

never let your system depend on any single component that can fail.

take a look at the improved arhitechture.

Everything that was single is now duplicated.

this is called redundancy

here before user reach your application

the call foes through Route53 (that is aws dns service (think of the dns as a phonebook of the internet that translate myapp.com to actuall address) but route 53 does more than the translation it continously look at the health of the infrasturcture (if it detects that i api gateway 1 dc1 is down it will redirect the traffic at api gateway 2 dc2) ) ->  load balaner 1 (zone 1) and load balancer 2 (zone 2) -> App servers, server 1 at location 1, server 2 at location 2, server 3 at location 3 (they are distributed acceoss different zones) -> database (primary database in region 1) and standby database in region 2 (both of them continuesly sync data to the primary)


now lets be honest, the redundancy is expennsive

for a small app this might be overkill, but let say for a banking system and ecomm platform or a healthcase system where downtime means lost revenue or danger to users its absoutely worth it.

single point of failure 

"If this component failes, does everything else survive" if the answer is no then its the single point of failure.
