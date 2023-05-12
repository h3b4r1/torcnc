# TorCNC
A system for setting up a Tor and SSH based CNC server using:
- Tor
- SSH
- AutoSSH
- termbin

## Components
### Client
Configures SSH over Tor with AutoSSH in order to automatically establish an outbound SSH tunnel over Tor to the CNC server. The tunnel can then either expose SSH allowing for reverse access back into the client or it can expose another service eg msfd. Additionally services can be bound to the loopback only, reducing the service visibility to external access.

### Server
Configures the server to expose SSH over Tor allowing for inbound SSH tunnels but preventing Shell access, as such the server can access the clients but the clients have limited access to the server, reducing the possibility that a compromised client could expose the server.
The client tunnels expose client service ports on the server loopback alowing for access to services or the CLI through SSH. 
Additionally automation tools such as ansible can be used to configure and manage clients once the session has been established.