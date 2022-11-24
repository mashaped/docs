# Example of unrolling a server via Docker Compose

[Docker](https://docs.docker.com/engine/install/) must be installed on the machine
as well as [Docker compose](https://docs.docker.com/compose/install/) plugin.

You should download the [docker-compose.yml](https://github.com/green-api/whatsapp-api-webhook-server-python/blob/master/docker-compose.yml) file. For example, using the command wget (Linux):

```
wget https://raw.githubusercontent.com/green-api/whatsapp-api-webhook-server-python/master/docker-compose.yml
```

Then you should compose the service from the image:

```
docker-compose build
```

and start it up:

```
docker-compose up
```

The commands should be run from the directory with the docker-compose.yml file
