Replication can be simply understand as the duplication and the copies of the data.
A system performance often depends on the database.
If the system database isn't available then most likely the system is not available.
If the database has high latency and low throughput then the system itself will have high latency and low throughput.
if you want to make high performance system you need to make the database is high performance.
this is where replication comes into the play

imagine if you have a single database and for whatever reasons the database goes down.

suddenly you cannot read or write data to your database.

so the entire system goes down.

to prevent this you can have a secondary database.
the replica of the main database.

the main database handle all the reads and writes and also updates the replica so the replica stays same as the main database.

so the main database goes down the replica take over.

and when the main database comes up its updated by the replica and becomes the main database again.

both of these databases needs to be in sync.

so when an update happens in the primary database. that update needs to be happen in the secondary database in a sync way. so the replica can take over the main database without any system inconsistencies.

if the write operation fails in the replica thhen it should not happen in the main database. It means the write operation will take long because it needs to happen in both main and replica database.

using replication helps us in the availability of the database.

we can also use replication to improve the database latency.

Example:

let's say we are designing a system like linkedin, where people write posts and other can read/interact with their posts.

Imagine we have a lot of user here in us and pakistan.

In that case we will have two databases, one in the us and one in the pakistan. Since these database located in the respestive regions they will experience low latency.

if i am in us and write a post, it will be wriitten in us database since, i've some of the connections in pakistan, my post needs to be replicated in the pakistani database as well. so that my posts can be seen to my followers or connection in pakistan.

since we're talking about feed here, we dont need to have a post instantly appear on the people feeds.

what we can do is that us database asyncronusly update the pakistani database. may be every minutes, every 5 minutes or 30 minutes.

in later point in time pakistan and us databases will update each other.
