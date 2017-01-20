# DevOps

## Linux nodes

A linux server should be setup with the following rules. These guidelines assume the server will be hosting some kind of system accessible over http/https.

 - A user called "iteam" having an authorized_keys file setup
 - SSH Root login disabled
 - SSH Password authentication disabled
 - Port 22 open
 - Port 80 and 443 open
 - All other ports closed

If any service on the node requires a non-http port to be opened, you need to carefully consider which external IP to allow connecting to it. In such case, configure the firewall to allow connections from those relevant IP addresses and nowhere else.

### SSH

SSH should have password authentication disabled. If it would have, there will be several thousand login attempts every week from all over the world. When setting up a new server, create a user called "iteam" and add the necessary public keys to /home/iteam/.ssh/authorized_keys

Edit /etc/ssh/ssd_config and set these two lines to "no"
```
PermitRootLogin no
PasswordAuthentication no
```

### firewall

In some of our environments the servers are hosted in managed environments where no ports are open to the world by default. In such case, opening ports to the world are done manually and likewise only ports 22, 80 and 443 should be opened (by necessity).

Servers hosted in some cloud environments however are open to the world by default (DigitalOcean for example). On such servers iptables can be used to setup firewall rules directly on the server.


TODO: Write example script
```
iptables
```