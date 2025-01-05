
> [!Definition]
> An event-driven architecture uses events to initiate actions and communication between decoupled services.

 An *event* is a change in state, a user request, or an update, like an item being placed in a shopping cart in an e-commerce website. When an event occurs, the information is published for other services to consume it. In event-driven architectures, events are the primary mechanism for sharing information across services. These events are observable, such as a new message in a log file, rather than directed, such as a command to specifically do something.

An _event_ is also an immutable fact that occurred in the past.

## Designing a Event Driven pattern

### Disadvantages of using a synchronous pattern

- Synchronous patterns do not account for failures and retries, the application should handle the retries of the failures and 

