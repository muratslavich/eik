# Stories

#### Primary developer on Escrow Order project. Developed a new application for more than 100 developer companies with more than 1000 users per day. Average 10000 orders per month.

I designed and developed the project from scratch. It's placed in the New Internet Bank cluster (200+ microservices).

Now the project contains 6 people.

Application for developer companies managers according to 214FZ for mortgage loans requests. The application allows to **create**, **sign by SMS**, **cancel order**, and see **list orders**. For clients who don't have bank accounts, we automatically **create an account**. For clients who have several accounts founded by ID information, we have a **back-office process**, for resolving this.

Order creation is the process with several steps such as:

* Creating order with draft status
* Depositor compliance checks
* Depositor creating (if the client has no account)
* Escrow account reservation
* Escrow account binding to developer account
* Create depositor order
* Send to sign

This steps logic is implemented in different services (some of it implemented by us, some already existed).

To perform distributed transactions I use the Saga pattern based on Kafka. \
The order creation produces an event in Kafka topic, that is listened by the Process Manager (separate microservice). \
The Process Manager performs all steps and commits Saga. \
All shared context keeps in the special Kafka topic. \
The failed step can be retried N times, after that, we perform rollback for the transaction. \
Because Kafka is "at least once" mechanism consumption, we keep all steps are idempotent. Of course, creation requests aren't idempotent, that why we have to handle errors when we try to create something twice.



We use bank core services on the enterprise bus like data store, so we don't have a relational database in the cluster.



Workflow:

* ...&#x20;



* Spring Boot
* Java 11 / Kotlin
* Kafka
* MongoDB
* Kibana
* Prometheus + Grafana
* Docker
* Mesos / Marathon
* Kubernetes
