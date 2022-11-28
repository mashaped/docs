# Python Webhook server library

#### Preparing environment
The latest version of Python 3 must be installed on the machine. It can be downloaded 
from the official web site: [python.org](https://www.python.org/downloads/)

#### Library installation

```
pip3 install whatsapp-api-webhook-server-python
```

#### Server startup

Just import the webhooksHandler to use it in your solutions
```
import whatsapp_api_webhook_server_python.webhooksHandler as webhooksHandler
```

Server start:
```
webhooksHandler.startServer('127.0.0.1', 80, onEvent)
```

onEvent - a method of webhooks processing defined by the developer.
It should have three parameters:
- webhooksHandler - library class instance
- typeWebhook - webhook type
- body - message body

Please see examplр [echo.py](https://github.com/green-api/whatsapp-api-webhook-server-python/blob/master/examples/echo.py)
