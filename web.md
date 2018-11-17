# Web

* What are the three primary Fielding constraints? (Bonus if you can say who Fielding is!)
    * Roy T Fielding is the originator of REST. wrote the PhD dissertation "Architectural Styles and the Design of Network-based Software Architectures
    1. Network must be made of clients and servers
    2. Stateless
        * Client does not need need to keep track of each other's state.
        * each request is treated as a standalone
    3. Uniform interface
        * common language between servers and clients that allows each part to be swapped out or modified without breaking the entire system
* What sub-constraints make up a Uniform Interface
    1. indentification of resources
        * each resource must be uniquely identified by a stable identifier
            * "stable" means does not change across interactions and does not change when state of resource changes
                * should return that request is bad if so
    2. manipulation of resources
    3. self-descriptive messages
    4. hypermedia
        * data sent from server to client that contains info about what client can do next aka further requests it can make
* Walk through an arbitrary example of a RESTful request/response cycle, and describe what makes it RESTful