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

![Simulate slow subscriber](image_1.png)
