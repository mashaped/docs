# Example of preparing the environment for Ubuntu Server

### Updating the system

Update the system:

```shell
sudo apt update
sudo apt upgrade -y
```

### Firewall

Set up the firewall:

Allow the SSH connection:

```shell
sudo ufw allow ssh
```

Base rules:

```shell
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Allow HTTP and HTTPS connections:

```shell
sudo ufw allow http
sudo ufw allow https
```

Enable the firewall:

```shell
sudo ufw enable
```

### Installation

Do not forget to create a module:

```shell
go mod init example
```

Installation:

```shell
go get github.com/green-api/whatsapp-api-webhook-server-golang
```

### Examples

Download and run our web server as an example:

Download Example:

```shell
wget https://raw.githubusercontent.com/green-api/whatsapp-api-webhook-server-golang/master/examples/main.go
```

Running the application:

```shell
go run main.go
```
