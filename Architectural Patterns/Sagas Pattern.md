
## Saga Choreography

The saga choreography pattern helps preserve data integrity in distributed transactions that span multiple services by using event subscriptions. In a distributed transaction, multiple services can be called before a transaction is completed. When the services store data in different data stores, it can be challenging to maintain data consistency across these data stores.

## Saga Orchestration

The saga orchestration pattern uses a central coordinator (_orchestrator_) to help preserve data integrity in distributed transactions that span multiple services. In a distributed transaction, multiple services can be called before a transaction is completed. When the services store data in different data stores, it can be challenging to maintain data consistency across these data stores.

**The prime difference between Saga Orchestration and Saga Choreography is how the participants are coupled. In an Orchestrator pattern, the participants are tightly coupled to the Orchestrator (Imagine a step functions workflow where we have a try catch method for compensating transactions) whereas for the choreography pattern we have all the services loosely coupled like an EventBridge bus with different rules triggering different services**

