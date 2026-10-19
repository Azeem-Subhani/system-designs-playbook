latency metrics: it plays a critical role in evaluating the performance of application and services.

by observing p90, p95 and p99 latencies

you can identify potential bottlenecks and improve user experiences and ensure that your system achieves high performance for the majority of the users.

Imagine you have a orcestrator api service which is connected to different micro-services and thrid part srevices, which perform special feature operation.

now for service including the orcestrator api
 - a latency must be calculated is that this particular api or srevics going to take perticular time
 - P90 latency signifies that, 90 percent of the request are completed within the given latency values while the remaining 10% took longer.
 - p95 reveals that 95% of the requst falls below the threshold.
 - p99 reveals that 99% of the request are recorded within the given latency. enabling you to identify the problems that affects a small percentage of the users.

 noticec we are talking about p90 and p95 and p99 not the p100 because there cannot be a p100.


 now for the p99

 if the SLA: latency values is 100ms -> then there will be 99 request that will take < 100ms and there is only 1 request that is greater than 100ms

 and lets say we have a arrays of the ms of the requests.

 [32,38,72,41,24,5,6,12,53,63,14,28,59,81,90,76,83,59,38,59,68,67,76,58,54,51]

 to calculate the p99 latency we first need to sort the data set in the ascending order.

 and we determine the position of the 99th percentile:

99% of 100 request would be 100 * 0.99 = 99
so the index position representing the 99th percentile is 99

that means 99 request received the response within 99ms.

and same algorithm for the p95 and p90.

answer when and why to p99 p95, and p90.

median.

we sort the dataset, then find the middle.

if dataset is odd number, we return the middle number
if dataset is event number, we take average of two middle values.
