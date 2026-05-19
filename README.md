# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To study on sliding window protocols.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
server.py
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000))
while True: 
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```

client.py
```
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
```
## OUPUT:
server:

<img width="865" height="302" alt="2b server" src="https://github.com/user-attachments/assets/7c3b172c-51de-466b-9783-dbc5fc862294" />

client:

<img width="798" height="302" alt="2b client" src="https://github.com/user-attachments/assets/48bc5bdb-02a3-4d08-a487-b0e857a6cdb4" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
