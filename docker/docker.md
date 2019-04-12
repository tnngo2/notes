# Dockers

## Manage docker as a non-root user
1. Create the docker group
```
$ sudo groupadd docker
```

2. Add the user to docker group
```
$ sudo usermod -aG docker $USER
```

## Configure Docker to start on boot

Most Linux distribution use systemd to manage starting services when the system boots.

```
sudo systemctl enable docker
```

## Configure 
By default, the Docker daemon listens for connections on a UNIX socket.
It is configurabled at "Bind Docker to another host/port or a unix socket"
[Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/dockerd/)

`#question` What is the Docker daemon?
