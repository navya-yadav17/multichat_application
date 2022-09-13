# multichat_application
Server Side Programming(Server.java)

1. Server class : The main server implementation is easy and similar to the previous article. The following points will help understand Server implementation :

The server runs an infinite loop to keep accepting incoming requests.
When a request comes, it assigns a new thread to handle the communication part.
The server also stores the client name into a vector, to keep a track of connected devices. The vector stores the thread object corresponding to the current request. 
The helper class uses this vector to find the name of recipient to which message is to be delivered. As this vector holds all the streams, handler class can use it to 
successfully deliver messages to specific clients.
Invoke the start() method.
2. ClientHandler class : Similar to previous article, we create a helper class for handling various requests. This time, along with the socket and streams, we
introduce a name variable. This will hold the name of the client that is connected to the server. The following points will help understand ClientHandler
implementation :

Whenever the handler receives any string, it breaks it into the message and recipient part. It uses Stringtokenizer for this purpose with ‘#’ as the delimiter. 
Here it is assumed that the string is always of the format: 
message # recipient
It then searches for the name of recipient in the connected clients list, stored as a vector in the server. If it finds the recipients name in the clients list, 
it forwards the message on its output stream with the name of the sender prefixed to the message. 











 A client should readily receive a message whenever it is delivered to it i.e sending and receiving must be implemented as separate activities rather than sequential.
There is a very simple solution which uses threads to achieve this functionality. In the client side implementation we will be creating two threads:

SendMessage : This thread will be used for sending the message to other clients. The working is very simple, it takes input the message to send and the recipient to 
deliver to. Note that this implementation assumes the message to be of the format message # recipient, where recipient is the name of the recipient. It then writes
the message on its output stream which is connected to the handler for this client. The handler breaks the message and recipient part and deliver to particular recipient.
Lets look at how this thread can be implemented.



readMessage : A similar approach is taken for creating a thread for receiving the messages. When any client tries to write on this clients input stream, we use 
readUTF() method to read that message.


















#deffie-Hellman algorithm
The Diffie–Hellman (DH) Algorithm is a key-exchange protocol that enables two parties communicating over public channel to establish a mutual secret without it being 
transmitted over the Internet. DH enables the two to use a public key to encrypt and decrypt their conversation or data using symmetric cryptography.
