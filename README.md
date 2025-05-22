# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
## CLIENT
```import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = socket.gethostname()  
port = 12345  
server_socket.bind((host, port))
server_socket.listen(5)
print(f"Server listening on {host}:{port}")
client_socket, client_address = server_socket.accept()
print(f"Connection from {client_address} has been established!")
while True:
    message_from_client = client_socket.recv(1024).decode('ascii')
    print(f"Client: {message_from_client}")
    
    if message_from_client.lower() == 'bye':
        print("Client has left the chat.")
        break

    message_to_client = input("Server: ")
    client_socket.send(message_to_client.encode('ascii'))

    if message_to_client.lower() == 'bye':
        print("Closing connection...")
        break

client_socket.close()
server_socket.close()
```

## SERVER 
```
import socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = socket.gethostname() 
port = 12345 
client_socket.connect((host, port))
print(f"Connected to server at {host}:{port}")
while True:
    message_to_server = input("Client: ")
    client_socket.send(message_to_server.encode('ascii'))

    if message_to_server.lower() == 'bye':
        print("Exiting chat...")
        break

    message_from_server = client_socket.recv(1024).decode('ascii')
    print(f"Server: {message_from_server}")

    if message_from_server.lower() == 'bye':
        print("Server has closed the chat.")
        break
    client_socket.close()
```
## OUPUT

![CREATION FOR CHAT USING TCP SOCKETS](https://github.com/user-attachments/assets/45f40351-d4f1-49c3-af56-de5243dfac62)


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
