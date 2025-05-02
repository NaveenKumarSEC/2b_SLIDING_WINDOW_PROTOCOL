# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To write a python program to perform sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
Sender:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send:"))
l=list(range(size))
s=int(input("Enter Window size:"))
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
```
Receiver:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgment received from the server".encode())

```

## OUPUT:
Sender:
![Screenshot 2025-04-12 142703](https://github.com/user-attachments/assets/78309c9f-c2af-4d82-a0fc-491c0f2f110d)

Receiver:
![Screenshot 2025-04-12 142714](https://github.com/user-attachments/assets/e1358c72-a090-4938-8be5-89a32a90665a)

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed
