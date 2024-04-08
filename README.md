# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
## PROGRAM - ARP
## client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter Logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
## client:
![Screenshot 2024-04-06 142506](https://github.com/Saranyaaav/2c.ARP_RARP_PROTOCOLS/assets/144870813/f8e89bc8-5f91-4cdf-ba71-a83901eef40b)
## server:
![Screenshot 2024-04-06 142529](https://github.com/Saranyaaav/2c.ARP_RARP_PROTOCOLS/assets/144870813/c65908c4-9981-4bab-a4e6-ee7142285a16)
## PROGRAM - RARP
## client:
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
## server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
## client:
![Screenshot 2024-04-06 144231](https://github.com/Saranyaaav/2c.ARP_RARP_PROTOCOLS/assets/144870813/ec39f747-2647-4727-a227-802d4bf8875b)
## server:
![Screenshot 2024-04-06 144334](https://github.com/Saranyaaav/2c.ARP_RARP_PROTOCOLS/assets/144870813/f4f3bc7c-9e62-4eeb-97bc-a196192ee267)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
