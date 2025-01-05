
Anti Corruption Layer pattern is a mediation pattern which is used while migrating a Monolithic to a microservices architecture.
It translates the model of the upstream bounded context (monolith) into a model that suits the downstream bounded context (microservice).

This reduces transformation risk and business disruption by preventing changes to callers when their calls have to be redirected transparently to the target system.

![[Anti Corruption layer pattern.png]]