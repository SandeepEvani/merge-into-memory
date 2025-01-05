
The scatter-gather pattern is a message routing pattern that involves broadcasting similar or related requests to multiple recipients, and aggregating their responses back into a single message by using a component called an _aggregator_. This pattern helps achieve parallelization, reduces processing latency, and handles asynchronous communication. It's straightforward to implement the scatter-gather pattern by using a synchronous approach, but a more powerful approach involves implementing it as message routing in asynchronous communication, either with or without a messaging service.

## Scatter by Distribution

In the scatter by distribution method, the root controller divides the incoming request into independent tasks and assigns them to available recipients (the _scatter_ phase). Each recipient (process, container, or Lambda function) works independently and in parallel on its computation, and produces a portion of the response. When the recipients complete their tasks, they send their responses to an aggregator (the _gather_ phase). The aggregator combines the partial responses and returns the final result to the client

## Scatter by Auction

If the controller isn't aware of the recipients or the recipients are loosely coupled, you can use the scatter by auction method. In this method, the recipients subscribe to a topic and the controller publishes the request to the topic. Recipients publish the results to a response queue. Because the root controller isn't aware of the recipients, the gathering process uses an aggregator (another messaging pattern) to collect the responses and distill them into a single response message. The aggregator uses a unique ID to identify a group of requests.