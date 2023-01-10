# Python Webhook server library

[![Python application](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-app.yml/badge.svg?branch=master)](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-app.yml)
[![Upload Python Package](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-publish.yml/badge.svg)](https://github.com/green-api/whatsapp-api-webhook-server-python/actions/workflows/python-publish.yml)

#### Configuration

Перед началом работы убедитесь, что вы выполнили настройку инстанса для получения вебхуков на ваш сервер [Personal area configuration](../../../api/receiving/technology-webhook-endpoint.md#cabinet).

- Перейдите в [консоль GreenAPI](https://console.green-api.com/)

- Создайте бесплатный инстанс на тарифе Developer

- В настройках инстанса укажите адрес вашего сервера вебхуков. Допускается указывать как доменное имя, так и IP-адрес

- Включите вебхуки, которые треубется получать. См. картинку в [настройках личного кабинета](../../../api/receiving/technology-webhook-endpoint.md#cabinet)

- Сохраните настройки инстанса

- Авторизуйте инстанс, считав QR-код с телефона

- Напишите любое сообщение в WhatsApp на номер, который подключен к инстансу

- Наблюдайте в консоли вебсервера входящие вебхуки сообщений

#### Server startup from the library

##### Preparing environment

- [Example of preparing a server environment on the Ubuntu operating system](serverUbuntu.md)

- [Example of preparing a server environment on the Windows operating system](serverWindows.md)

##### Library

- [Whatsapp-api-webhook-server-python library](serverLibrary.md)

#### Server startup in Docker

- [Example of unrolling a server environment in a Docker container](serverDocker.md)
- [Example of unrolling a server via Docker Compose](serverDockerCompose.md)
- [Example of unrolling a server in a Docker container on Yandex Cloud](serverDockerOnYandexCloud.md)