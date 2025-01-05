The hexagonal architecture pattern, which is also known as the ports and adapters pattern, was proposed by Dr. Alistair Cockburn in 2005. It aims to create loosely coupled architectures where application components can be tested independently, with no dependencies on data stores or user interfaces (UIs). This pattern helps prevent technology lock-in of data stores and UIs. This makes it easier to change the technology stack over time, with limited or no impact to business logic. In this loosely coupled architecture, the application communicates with external components over interfaces called _ports_, and uses _adapters_ to translate the technical exchanges with these components.

**Pros**:
- Easy Testability
- Easy Maintainability

**Cons**:
- Complexity in writing code
- Latency in communication between the microservices
- Hardships testing locally

