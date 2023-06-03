EX-3 IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
DATE : 23/03/2023
AIM :
To write a python program to perform sliding window protocol

ALGORITHM :
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client otherwise it
will send NACKsignal to client.
6. Stop the program
PROGRAM :
CLIENT PROGRAM :
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
 while(i<len(l)):
 st+=s
 c.send(str(l[i:st]).encode())
 ack=c.recv(1024).decode()
 if ack:
 print(ack)
 i+=s

SERVER PROGRAM :
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())

OUTPUT :
CLIENT OUTPUT :
![cli3](https://github.com/Praveenanagaraji22/EX-3/assets/119393514/45acfa59-b829-4e3a-868d-1137cb169f9f)


SERVER OUTPUT :
![ser3](https://github.com/Praveenanagaraji22/EX-3/assets/119393514/2481c487-a05f-4da4-97c2-064ccc64b18c)


RESULT:
Thus, python program to perform sliding window protocol was successfully executed.
