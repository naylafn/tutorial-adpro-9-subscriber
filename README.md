# Tutorial Pemrograman Lanjut
## Nayla Farah Nida - 2306213426

### Module 9

**Understanding subscriber and message broker**

a. What is amqp?

AMQP stands for Advanced Message Queuing Protocol.
It is an open standard protocol for message-oriented middleware that enables systems to communicate with each other by sending and receiving messages.
AMQP works by allowing applications to communicate through a central message broker. Message broker is used to manage message queues and delivery between producers and consumers.
A producer sends a message to the broker, which then routes it to the appropriate queue based on defined rules.
Consumers listen to these queues and process the messages when they arrive. This setup enables asynchronous communication, meaning producers and consumers don’t need to run at the same time.
It also makes systems more reliable, as messages can be stored in queues until they’re successfully handled.

b. What does it mean? ```guest:guest@localhost:5672```, what is the first guest, and what is the second guest, and what is ```localhost:5672``` is for?  

The string ```guest:guest@localhost:5672``` is a connection URI used to connect to an AMQP server following the format ```protocol://username:password@hostname:port```.
So in short, the string is for connecting to an AMQP server running on the computer, using the username guest and password guest, through the AMQP port 5672.

**Simulation slow subscriber**

Number of messages in the queue is above 20 because messages are published faster than they are consumed, it decreases as the subscriber slowly processes the messages.
Each cargo run in the publisher sends 5 messages quickly to RabbitMQ. But the subscriber is slow, taking time to process each message because of the sleep, so RabbitMQ starts queuing messages that the subscriber hasn’t picked up yet.

![Simulate slow subscriber](image_1.png)

**“Reflection and Running at least three subscribers**

When I run three subscriber instances, I create three consumers competing to receive messages from the same queue. This is called a competing consumer pattern in messaging systems like RabbitMQ.
Publisher sends messages into a single queue (user_created), then RabbitMQ distributes those messages across the 3 subscribers. Each subscriber gets roughly 1/3 of the messages (round-robin by default). All 3 subscribers process messages in parallel. Because of this parallel processing, the queue empties more quickly.

![Running 3 subscribers](image_2.png)
