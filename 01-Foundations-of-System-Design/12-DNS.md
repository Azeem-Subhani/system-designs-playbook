The Domain Name System DNS is the internet directory.

It translate human readable domain names such as youtube.com

to the ip address.

www.youtube.com -> 208.65.153.238


DNS could be quite confisuing because there are various type of dns servers within the dns hirarchy.

every device connected to  the internet has a unique ip address,
that look something like this: 202.64.153.245


but who want to remember a long number everything they want to visit a website.


thats where domain names comes in

they are human friendly name like youtube.com

when you type domain name in the browser, the dns server figure out ip address, and diirects your request to the right server.

The main functionality that dns provides, it collects a huge database, which converts dns names to ip address,

verisign manages database of all registered domain names.

as of today there are more than 350 millions domain registered arround the world.


when your browser makes a dns query it contacts the dns resolver.

this DNS resolver can be provided by your ISP, or cloudflare or the google dns resolver.

if the dns resolver doesn't have the answer in its cache, it finds the right authoritative nameserver. (the authritative names server is the one who holds the answer.)


how the resolver rocalte the authoritative names server: 


Useually there are three types of DNS servers

 - Root Namesservers
 - TLD Nameservers
 - Authoritative Nameserver

 nameserver are specific type of servers with specific job.

in this case resolving domain names to ip servers.

there are 13 root nameservers globally, they form the foundations of hirarchy.

anything you do a dns query you will routed to the one closer to your location.


root name servers stores the ip addresses of the TLD names servers.

TLD nameservers hold the ip addresses of the authoritative names server

authoritative nameserver are the final source of truth of dns record related to a specific domains.

they hold the most accurate up to date ip addresses of the domains and sub domains.



you type the 'youtube.com' in the browser, the browser checks it cache for the ip address, if not found it check the operating systems, router and event isp dns cache in sequence.

If the ISP dns server doesn't have the ip address the quries the dns server. which goes to root dns server then the root level server directs the query to top level domain servers, (
the TLD responsible for top level domain like .com, .pk .org .lol) then top level domain servers to the authritative server for the youtube.com they return the ip address of that domain.

finally the browser receive the ip address and you're able to connect to the youtube server.
