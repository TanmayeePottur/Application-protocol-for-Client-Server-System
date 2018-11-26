# Application-protocol-for-Client-Server-System
The basic objective of this project is to show the working of an application protocol for knock knock joke as the communication between the client and the server. Here, we use the TCP (transmission control protocol) as we shall require a file transfer of data which uses TCP, also, a delay of messages is not appreciable. This protocol uses TCP sockets and the port number used here is 3897. Henceforth, the port numbers should be between this range. However, we do not require any encryption or security for a simple knock-knock joke. The communication between the client and server where the client is a human-user(mostly) and the server responds, which is as follows:

Client:  Hello server!
Server: Hello there client! Have a joke?
Client: Knock-knock!
Server: Who’s there?
Client: Ya.
Server: Ya who?
Client: I’m excited to see you too!
Server: Ha-ha. Good one. How about another one?

The above conversation is the typical example of how the conversation would go. The client sends a request by sending the message “Hello server!” and the server replies “Hello there client! Have a joke?”. This ensures the client to go ahead and tell the joke. This satisfies the handshake from the server of receiving the message. The above responses from both the client and server are a MUST and the client must respond with “Knock-knock!” (Any other case will not be accepted) and the server must respond with “Who’s there?” (any variation of this message will not be accepted - capital ‘W’, ‘s, ‘?’ at the end), which then continues the conversation of the knock knock joke. However, according to the protocol, the joke must be completed and the server replying three times is a general condition to do so, as all knock-knock jokes are typically three-four lines long.
The following exception conditions show the exact error message ex: “E001- joke incomplete”
Exception conditions:
I.	The server may initially itself decide to not respond which ensures the joke is incomplete or no handshake. In that case the server throws an exception. General condition is when the server doesn’t respond three times. (Error code- E001—joke incomplete)
II.	An exception is thrown when the joke is not completed or there is a variation of the spelling or punctuation exception. This happens when the server doesn’t encounter “s”, “?”, “!”, “-“. Any variation other than the exact same message being “Who’s there?”and “Knock-knock”. (Error code- E002—Variation of spelling or punctuation exception). 
III.	An exception may also be thrown if the port is already in use and the client and server try to access it. (Error code- E003 Port already in use)--- this message would not be sent to the user.
IV.	When the server takes a very long time than the time window defined, an exception is thrown. The time window for response is defined as 15 seconds. (Error code- E004 Timeout)  

The above scenarios are as follows:

Scenario I (E001—joke incomplete)
Client:  Hello server!
Server: Hello there client! Have a joke?
Client: Knock-knock!
Server: Who’s there?
Client: Ya.
  (server doesn’t respond incomplete joke)

Scenario II (E002—Variation of spelling or punctuation exception)
Client:  Hello server!
Server: Hello there client! Have a joke?
Client: Knock knock
  (Exception thrown as server did not detect “-“ and “?”)

Scenario III (E003)
In this condition, the both client and server try access the same port and hence an exception is thrown, and the conversation doesn’t go forward. The error message is not sent to the client, but is there between the windows being used.
Scenario IV (E004)
Client:  Hello server!
Server: Hello there client! Have a joke?
Client: Knock-knock!
  (server doesn’t respond in the given time window timeout exception is thrown)

The client may end the conversation by replying negatively to the server after the initial joke is finished to discontinue the conversation by replying “no” to the question “Ha-ha. Good one. How about another one?”. 
We consider that the client and server may make mistakes in the responses and hence defined the variations and the joke must be finished as we have stated before.
