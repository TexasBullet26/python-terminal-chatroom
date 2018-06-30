# Python Terminal Chatroom
---
A simple python terminal chatroom program that includes a chat server and a client script.

**Required**: `python v2.7`

## Directory Structure
---
- python_chat/
  - client/
    - client.py (Implements the client-side of the chat room)
  - server/
    - chat_server.py (Implements server-side of the chat room)
---

## Usage
---
The server can be ran on a LAN by choosing any computer (has to be on) to be the server node. Use that computer's private IP address as the server IP address.

For example:
  - If a LAN has a set of private IP addresses that are assigned ranging from 192.168.1.2 - 192.168.1.100, then any computer from these 99 nodes can act as a server. The remaining nodes may connect to the server node by using the server's private IP address.
  - Be careful choosing a port that is currently not in use (port 22 and port 80 shouldn't be used).

If the server is going to be accessible beyond a local network (LAN), the public IP address is required for usage. This would require port forwarding in cases where a node from a local network (node that is not the router) wishes to host the server.
  - In this case, we would require any requests that come to the public IP addresses to be re-routed towards our private IP address in our local network (LAN). This requires port forwarding.

To run, download the scripts from this GitHub repo and save them on your computer wherever you wish.

## How to Run the Chat
---
The server-side script (chat_server.py) must be ran at all times to keep the chatroom running.

You can run both the server and client scripts from the command prompt (Windows) or from bash (Linux). First start the chat server:

```bash
python <SCRIPT> <IP_ADDRESS> <PORT>
```

For example:

```bash
python chat_server.py 192.168.1.65 8082
```

Once the server is up and running, you can start the client script:

```bash
python <SCRIPT> <IP_ADDRESS> <PORT>
```

For example:

```bash
python client.py 192.168.1.65 8082
```

Each user must use the client-side script (client.py) in order to connect to the server.

The client-side script will attempt to access the server socket created at the specified IP address and port. Once it connects, it will continuously check as to whether the input comes from the server or from the client, and redirects output accordingly. If the input is from the server, it displays the message on the terminal. If the input is from the user, it sends the message that the user enters to the server for it to be broadcasted to other users.
