# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To implement a program to illustrate the mechanism of sliding window protocol
## PROGRAM
Developed by : ASWIKA B
Reg no : 212224220013
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program

Client
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
Server
```
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())

```
## OUTPUT:
<img width="1037" height="390" alt="Screenshot 2025-11-16 190521" src="https://github.com/user-attachments/assets/89c3d59b-9763-4d0f-80cb-3d9d92272f49" />
<img width="1040" height="293" alt="Screenshot 2025-11-16 190548" src="https://github.com/user-attachments/assets/7a57c991-79fd-46c3-9bde-4de920d47624" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
