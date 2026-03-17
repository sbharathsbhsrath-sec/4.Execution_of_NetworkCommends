# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
##Program

```
#server
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
#client
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
## Output
<img width="1004" height="325" alt="image" src="https://github.com/user-attachments/assets/0bbf1dab-4c52-41fe-a9ee-62e9c3347ae0" />
<img width="964" height="235" alt="image" src="https://github.com/user-attachments/assets/29a9830c-f4b2-4f56-a49f-82e2fecd7391" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c278c676-0f46-4829-821c-497721f925e1" />
<img width="1033" height="775" alt="image" src="https://github.com/user-attachments/assets/79dbf7c5-0335-4931-a4cb-dd0ea89b50ab" />
<img width="694" height="521" alt="image" src="https://github.com/user-attachments/assets/08572653-1bcd-488b-b4ed-c244625c655b" />
<img width="994" height="422" alt="image" src="https://github.com/user-attachments/assets/2bd6861d-4e36-4b0a-b765-8d76f8d6e802" />
<img width="1536" height="941" alt="image" src="https://github.com/user-attachments/assets/eac82470-9fea-45c7-9368-98f929fd5b67" />

## Result
Thus Execution of Network commands Performed 
