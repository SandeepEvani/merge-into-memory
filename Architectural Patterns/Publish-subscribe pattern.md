
The publish-subscribe pattern, which is also known as the pub-sub pattern, is a messaging pattern that decouples a message sender (_publisher_) from interested receivers (_subscribers_). This pattern implements asynchronous communications by publishing messages or events through an intermediary known as a _message broker_ or _router_ (message infrastructure). The publish-subscribe pattern increases scalability and responsiveness for senders by offloading the responsibility of the message delivery to the message infrastructure, so the sender can focus on core message processing.

SNS and EventBridge are the two services which can be used for the pub-sub pattern.

EventBridge offers more flexibility compared to SNS, like event transformation, archive and replay capabilities etc.., EventBridge can act an Event Router whereas SNS is more like an event broadcaster




