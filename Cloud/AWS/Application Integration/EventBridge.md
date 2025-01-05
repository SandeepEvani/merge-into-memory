[[Application Integration]]

> [!Definition]
> Amazon EventBridge is a serverless event bus service that makes it easier to build event-driven applications at scale using events from your applications, integrated SaaS partners, and AWS services. You can deliver events to many AWS services, including AWS Lambda and Amazon Simple Notification Service (Amazon SNS), and other SaaS applications.


EventBridge is a fully managed service that handles event ingestion, delivery, security, and authorization. Using EventBridge, you decouple event producers from event consumers, so each component of the system can independently scale while events are filtered and routed. EventBridge makes it easier to integrate services without needing custom integration logic to connect to individual services.

## Key Components of EventBridge

- Event: An event is an indicator of change in state, Events are immutable facts that have occurred in the past.
- Event bus: An event bus is a pipeline that receives events.
- Rule: A rule matches the incoming events and matches them to the appropriate targets for processing
- Target: A Target is a resource where the matched events are pushed to.



