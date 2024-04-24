# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## SOFTWARE : Command Prompt And Network Protocol Analyzer
## PROCEDURE: To do this EXPERIMENT- follows these steps:
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

## PROGRAM:
## PING COMMAND:
### CLIENT:
```
import socket
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
    c,addr=s.accept()
    print("Connecting from ",addr)
    try:
        hostname=c.recv(1024).decode().strip()
        if hostname:
            try:
                response=str(ping(hostname,verbose=True))
                c.send(response.encode())
            except Exception as e:
                c.send("ping failed  {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error: ",e)
    finally:
        c.close()
```
## SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
    while True:
        ip= input("Enter Website u want to ping :")
        s.send(ip.encode())
        response=s.recv(1024).decode()
        if response:
            print ("Ping result :",response)
        else:
            print ("No response from server")
except Exception as e:
    print ("Error:", e)
finally:
    s.close()
```
## TRACEROUTE COMMAND:
```
from scapy.all import* 
target = ["www.google.com"] 
result, unans = traceroute(target,maxttl=32) 
print(result,unans)
```
## OUTPUT:
### CLIENT:
![image](https://github.com/Gokztechz/4.Execution_of_NetworkCommends/assets/117667038/9541d006-b657-4474-b61a-b1ac16d9f1fc)
### SERVER:
![image](https://github.com/Gokztechz/4.Execution_of_NetworkCommends/assets/117667038/0a483ced-7f31-47e5-a06f-584d6e161fc5)
### TRACEROUTE COMMAND:
![image](https://github.com/Gokztechz/4.Execution_of_NetworkCommends/assets/117667038/0f2b9edd-9d97-4595-bba3-b9553e6b4a5e)






## RESULT:
Thus Execution of Network commands Performed.
