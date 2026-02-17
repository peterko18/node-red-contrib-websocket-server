

[![Node-red](https://img.shields.io/badge/Platform-Node--Red-red?style=for-the-badge
)](https://nodered.org/)
[![Apache2](https://img.shields.io/badge/License-Apache--2.0-brightgreen?style=for-the-badge
)](https://www.apache.org/licenses/LICENSE-2.0)
[![Websocket](https://img.shields.io/badge/Protocol-Websocket-darkgreen?style=for-the-badge
)](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)

# node-red-contrib-websocket-server
Node for run Websocket server with some aditional features

## Core
Based on Node-Red inbuild websocket node 

## Install
Run the following command in your Node-RED user directory - typically `~/.node-red`
```bash
    npm install node-red-contrib-websocket-server
```

## Nodes

#### Websocket_server
 Settings:  
- Path - Websocket server address  

  `ws(s)://<your node-red address>:<node-red Port>/"Path"` 

- Send/Receive - msg format
  - payload - only msg.paylod will be processed  
  - Entire message - full msg object will be processed

- Ping action  
  - none - Automatically answer on Ping request from Client
  - Send ping - Server send ping every x seconds (require "Send ping interval" option >0)
  - Receive ping - Server is waiting for incoming ping from Client.  If interval between two ping requests is greater than x seconds (require "Receive ping timeout" option >0) connection will be closed by server.

#### Websocket_in - node for receive websocket messages
- Path - You can connect it to already existing server Path or create new server 
- Name - Optional Node Name
#### Websocket_out - node for send websocket messages
- Path - You can connect it to already existing server Path or create new server 
- Name - Optional Node Name
  #### Input - require msg object with `.payload`
  Optional - msg._session
  - to send message to group of clients msg._session = [client1_id, client2_id, ...]
  - to send message to one client msg._session = client_id or msg._session.id = client_id
  - if no msg_session, message is sent to all connected clients
#### Websocket_Open/Close - Information node about connection status 
- Path - You can connect it to already existing server Path or create new server 
- Name - Optional Node Name
  #### Output - `{msg.event : open or close, msg._session : {id : websocket id, type : 'websocket'}}`

#### Websocket_Drop - node to forcefully close websocket by id
- Path - You can connect it to already existing server Path or create new server 
- Name - Optional Node Name
  #### Input - require msg object with `._session.id`

## TODO
- Clean code
- Add tips in nodes
- In Websocket_Open/Close add reason for close event
  


