# Example of preparing a server environment on the Ubuntu operating system

After creating a machine for the server, you have to configure a firewall on it, install the necessary components and start up the server.

Ubuntu 20.04 and higher are supplied with Python 3 pre-installed .
Update the system:
```
sudo apt update
sudo apt -y upgrade
```

You should set up firewall rules. In Ubuntu, the UFW firewall is installed by default, but if for some reason it is not installed, install it:
```
sudo apt install ufw
```

First, create the default firewall rules:
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

If we activate the UFW firewall at this stage, all incoming connections will be denied.
We should add rules to be able to connect via SSH after activating the firewall:
```
sudo ufw allow ssh
```

HTTP connections on port 80 that are used by non-encrypted web servers, use the command:
```
sudo ufw allow http
```

HTTP connections on port 443 that are used by encrypted web servers, use the command: 
```
sudo ufw allow https
```

If your server has a public network interface named eth0, you can allow HTTP traffic (port 80) to that interface with the following command:
```
sudo ufw allow in on eth0 to any port 80
```

You can find the network interface name using the command:
```
ip addr
```

UFW firewall activation:
```
sudo ufw enable
```

Now our server can accept incoming requests on the port we have specified.

Install the pip package management system if the OS distribution doesn't contain it:
```
sudo apt install -y python3-pip
```

Теперь можно устанавливать нашу библиотеку.

Установка библиотеки:
```
pip3 install whatsapp-api-webhook-server-python
```

Можно в качестве примера запустить на сервере наш скрипт echo.py, он будет выводить в консоль информацию о полученных вэбхуках:
```
wget https://raw.githubusercontent.com/green-api/whatsapp-api-webhook-server-python/master/examples/echo.py
python3 echo.py
```
