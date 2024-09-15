- Strong Consistency and Async Process do not go hand in hand
- There are only two ways consumer can consume something from queue/broker.
	- Pull based --> Kafka, SQS
	- Push based --> real time PubSub

#### Fundamental Difference Between Stream and Broker
- If we want to process a message multiple times by multiple **types** of consumer, then we go with **Message Streams** (for e.g. Kafka, Kinesis)
- If we want one message to be consumed by only one type of consumer, not exactly one time processing we are talking about here, then we will go with **Message Queue**
