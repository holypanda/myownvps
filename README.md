# My own vps
Detail instruction for constructing own vps.
## Server Envirement
Server: Google Cloud  
OS: Ubuntu 16.04  
Make sure to allow access to all port in Google firewall  
## Install SS Server:
```
  sudo -i
  apt-get update
  apt-get upgrade
  
  # Python 3
  apt-get install python3
  apt-get install python3-pip
  python3 -m pip install shadowsocks
  # Python 2
  apt-get install python
  apt-get install python-pip
  python -m pip install shadowsocks
```
## Configure ss
  Make config file direction:
```
  mkdir /etc/shadowsocks
  vim /etc/shdowsocks/config.json
```
  Single-user:
```
  {
  "server":"myseverip",  
  "server_port":8388,
  "local_address":"127.0.0.1",
  "local_port":1080,
  "password":"mypassword",
  "timeout":300,
  "method":"rc4-md5",
  "fast_open":false
  }
```
  Multi-user:
```
  {
  "server":"myseverip",
  "local_address":"127.0.0.1",
  "local_port":1080,
  "port_password":{
  "port-1":"userpwd-1",
  "port-2":"userpwd-2"
  },
  "timeout":300,
  "method":"aes-256-cfb",
  "fast_open":false
  }
```
## Start the SS Server:
```
to start:
ssserver -c /etc/shdowsocks/config.json -d start

to stop:
ssserver -c /etc/shdowsocks/config.json -d stop
```

Quick-Start without config:
```
ssserver -p 8000 -k password -m rc4-md5 -d start
```

Boot-Start:
Add the start sever command to the /etc/rc.local file
```	
vim /etc/rc.local
```
