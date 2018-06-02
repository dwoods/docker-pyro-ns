# Pyro4 Name Server

Image on DockerHub: [farshidtz/pyro4-ns](https://hub.docker.com/r/farshidtz/pyro4-ns/)

Source repository: [github.com/farshidtz/docker-pyro-ns](https://github.com/farshidtz/docker-pyro-ns)

This image starts a [Pyro4 Name Server](https://pythonhosted.org/Pyro4/nameserver.html).

## Usage

The Pyro name server is bound to `localhost` by default which means other containers and the host machine will not be able to reach it from outside the container. To avoid that the name server must be bound to a hostname.

The following command will run a container with hostname `pyro-ns` and executes the name server bound to it.
```
docker run -p 9090:9090 -h pyro-ns farshidtz/pyro4-ns --host=pyro-ns
```

Use the nat configuration if you want to access the name server from the host machine:
```
docker run -p 9090:9090 -h pyro-ns farshidtz/pyro4-ns --host=pyro-ns --nathost=localhost --natport=9090
```

For other arguments, refer to [here](https://pythonhosted.org/Pyro4/nameserver.html#starting-the-name-server).

Using the name server control tool, you can check if the name server is running and accessible:
```
$ pyro4-nsc list
--------START LIST
Pyro.NameServer --> PYRO:Pyro.NameServer@pyro-ns:9090
    metadata: [u'class:Pyro4.naming.NameServer']
--------END LIST
```