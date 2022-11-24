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

HTTP connections on port 80 that are used by non-encrypted web servers, using the command:
```
sudo ufw allow http
```

Соединения HTTPS на порту 443, которые используются веб-серверами с шифрованием, с помощью команды: 
```
sudo ufw allow https
```

Если на вашем сервере имеется публичный сетевой интерфейс под названием eth0, вы можете разрешить трафик HTTP (порт 80) для этого интерфейса с помощью следующей команды:
```
sudo ufw allow in on eth0 to any port 80
```

Название сетевого интерфейса можно узнать с помощью команды:
```
ip addr
```

Активация брандмауэра UFW:
```
sudo ufw enable
```

Теперь наш сервер может принимать входящие запросы на указанный нами порт.

Установим систему управления пакетами pip, если он не содержиться в дистрибутиве ОС:
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
