# EX-5 IMPLEMENTATION OF REVERSE ADDRESS RESOLUTION PROTOCOL ( RARP )

DATE :

AIM:

To write a python program for simulating RARP protocols using UDP

ALGORITHM:

Client

1. Start the program
2. Using datagram sockets UDP function is established.
3. Get the MAC address to be converted into IP address.
4. Send this MAC address to server.
5. Server returns the IP address to client.


Server

1. Start the program.
2. Server maintains the table in which IP and corresponding MAC addresses are stored.
3. Read the MAC address which is send by the client.
4. Map the IP address with its MAC address and return the IP address to client.


PROGRAM:

CLIENT:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode()) 
 ```
SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
REG NO:
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
 ```
OUTPUT:

CLIENT:
![image](https://github.com/Subalakshmisuresh/EX-5/assets/121957896/ac60bae3-498f-47a4-9cb6-7808fbad3137)


SERVER:
![image](https://github.com/Subalakshmisuresh/EX-5/assets/121957896/a213a8b9-c5e1-4b7e-a9d1-719c1978d28a)


RESULT:

Thus, python program for simulating RARP protocols using UDP was successfully executed.
