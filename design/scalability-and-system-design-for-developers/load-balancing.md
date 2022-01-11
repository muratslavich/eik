# Load balancing

* distribute heavy traffic across the servers running in the cluster based on several algorithms.
* if the node goes down LB routes the future requests to other up and running nodes in the cluster.
* single point of contact for all the client requests.
* LB can be set up to manage traffic towards any component (back app, databases, queues, and other)



### Health checks

To ensure LB route requests to up and running servers, LB regularly perform health checks.

![](<../../.gitbook/assets/image (7).png>)

* in-service machines
* out of service



