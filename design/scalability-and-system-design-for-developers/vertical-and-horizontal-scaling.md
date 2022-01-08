# Vertical and Horizontal Scaling

**Vertical scaling** - Is adding more resources (adding memory). The simplest one. Do not have to touch the code or make any complex distributed system configurations. There is always a **risk of them going down** and the entire website going offline.

**Horizontal** - adding more hardware to the pool. This increases the computational power of the system as a whole. Add more servers/data centers to have the ability to **dynamically scale** in real-time as the traffic increases and decreases over a period of time. **High availability** of the system.

&#x20;**Cloud computing.**\
The biggest reason why _cloud computing_ become so popular in the industry is the ability to scale up and down dynamically. The ability to use and pay only for the resources required by the website became a trend for obvious reasons.

Distributed environment requires **administrative, monitoring, logging** efforts.



### Code maintaining

In distributed environment application has to be **stateless**. No static/state instances in classes that hold application data. Use key-value store to hold data. That's why functional programming became so popular - the function doesn't have state.





