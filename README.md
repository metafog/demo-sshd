<div align="center">
<img src="https://planetr.io/img/logo-github.png"></img>
</div>

# Planetr Demo: demo-sshd
Access the decentralized container through SSH client.

## Docker usage on local machine 
```
docker run -ti -p 2222:22 planetrio/demo-sshd
```

Access via any SSH client

```ssh planetr@localhost -p 2222```
password: ```planetr789```

## Deploy and run the same docker image on Planetr decentralized cloud

[Install and run](https://planetr.io/getstarted.html) the Planetr gateway node

Create and run a decentralized compute unit (DCU) on Planetr network

```
$ planetr dcu-run -p 2222:22 planetrio/demo-sshd g.micro
INSTANCE ID STATUS TYPE IMAGE NAME PORTS CREATED AT
c1tbgjf2hraqacl2ouq0 Pending g.micro planetrio/demo-sshd 2222:22 2021-04-17T15:58:29.791084+05:30
```

Please wait for the status to become 'Running'. This docker image has ```SSHD``` daemon running with a user ```planetr```

```
$ ssh planetr@localhost -p 2222
```

Enter password ```planetr789``` and you are logged in with SSH! Play around with linux commands and 'exit' to come out of the ssh shell

Delete the DCU.
```
$ planetr dcu-rm c1tbgjf2hraqacl2ouq0
INSTANCE ID STATUS TYPE IMAGE NAME PORTS CREATED AT
c1tafjn2hraq06kud0bg Deleting g.micro planetrio/demo-sshd 2222:22 2021-04-17T14:48:06.568676+05:30
```

Check status again.

```
$ planetr dcu-ps
INSTANCE ID STATUS TYPE IMAGE NAME PORTS CREATED AT
```

## Docker Build (If in case)
```
docker build -t planetrio/demo-sshd .
```
