# Example of unrolling a server environment in a Docker container

[Docker](https://docs.docker.com/engine/install/) must be installed on the machine.

To get an image from DockerHub, use the command:

```
sudo docker pull greenapi/whatsapp-api-webhook-server-python
```

Run the image in a container specifying the port and displaying the console:

```
sudo docker run --publish 8080:80 -it greenapi/whatsapp-api-webhook-server-python
```

You can specify any free port on the machine instead of port 8080. You should identify IP (or the machine external name) specifying this port in the console of the [Green-Api personal area](https://console.green-api.com/instanceList/) нужно будет указать IP (or the machine external name) specifying this port.

After the container startup, webhooks should come to the container console.
