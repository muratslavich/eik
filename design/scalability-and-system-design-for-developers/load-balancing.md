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



### DNS load balancing

* Enable [The authoritative server](../../web/dns.md) to return list IP addresses of a domain to the clients.
* With every request, the authoritative server changes the order of the IP addresses in the list in a round-robin manner.
* Client send request to the first IP address on the list&#x20;
* In case if the first doesn't return a response, client can send request to the next one.&#x20;
