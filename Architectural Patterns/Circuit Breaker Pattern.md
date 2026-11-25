
The circuit breaker pattern can prevent a caller service from retrying a call to another service (_callee_) when the call has previously caused repeated timeouts or failures. The pattern is also used to detect when the callee service is functional again.

Refer to this [link](https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/circuit-breaker.html#circuit-breaker-implementation) for additional information.