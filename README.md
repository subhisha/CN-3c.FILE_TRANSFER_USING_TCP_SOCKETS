# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## server.py
```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()

s.bind((host, port))
s.listen(5)

while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = r'C:\Users\acer\mytext.txt'
    f = open(filename, 'rb')

    l = f.read(1024)

    while l:
        conn.sendall(l)
        print('Sent ', repr(l))
        l = f.read(1024)

    f.close()
    print('Done sending')

    conn.close()
    break

s.close()
```
## Client.py
```
import socket

s = socket.socket()
host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open(r'C:\Users\acer\received_file.txt', 'wb') as f:
    print('Receiving data...')

    while True:
        data = s.recv(1024)

        if not data:
            break

        f.write(data)

print('Successfully received the file')
s.close()
print('Connection closed')
```
## OUPUT
## SERVER 
<img width="1033" height="277" alt="image" src="https://github.com/user-attachments/assets/c8a35049-93fd-4f1c-a526-56ccf8f5142d" />
## Client 
<img width="1042" height="206" alt="image" src="https://github.com/user-attachments/assets/b6b2ed1b-b017-43ed-bed4-fc918d18fc56" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
