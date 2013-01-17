Message-Driven-Bean---EJB-Example
=================================

A simple example to illustrate that message-driven javabeans can be used to implement any messaging type, typically JMS (Java Message Service API). To fully understand this code, you should be familiar with the concepts of queues and message.


When these 2 classes are used to build a netbeans or ant project, we get a simple messaging application. It has mainly two components:

<code>SimpleMessageClient:</code> An application that sends several messages to a queue.<br>
<code>SimpleMessageBean:</code> A message-driven bean that asynchronously receives and processes the messages that are sent to the queue. <br>


The client class sends messages to the queue that the bean class listens to. The client starts by injecting the connection factory and queue resources. Thereafter, it creates the connection, session and message producer. Finally, the client sends multiple messages to the queue. 

The bean class is coded with some MDB requirements (MDB annotation, public declaration, public constructor) in mind. It implements the message listener interface for the messaging type it is supposed to support, which in our case is JMS. When the queue receives a message, the EJB container invokes the listener method(s) in this class. Its called the <code>onMessage</code> method. This method contains the business logic that handles the processing of the message. It is the MDB's task to parse the message and perform the necessary business logic. This method takes in a single argument: the incoming message from the queue. Our bean class takes in the incoming message, casts it to a text message and displays it on the screen.

These 2 java files can be packaged as a .EAR file, deployed and run via NetBeans or Eclipse. Or you can simply use Maven or Ant to do it via the command line.
