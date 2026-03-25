# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## SERVER
```
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
```
## CLIENT
```
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st
```

## OUPUT

SERVER

<img width="337" height="116" alt="Screenshot 2026-03-25 192346" src="https://github.com/user-attachments/assets/0d49992c-3115-4ca9-8a2f-3f071ca6e7b4" />

CLIENT

<img width="549" height="169" alt="Screenshot 2026-03-25 192334" src="https://github.com/user-attachments/assets/387fc92f-49c0-406d-8cf3-00bb7107b4ce" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
