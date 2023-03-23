# Golang Webhook Server Library

[![license](https://img.shields.io/github/license/green-api/whatsapp-api-webhook-server-golang)](https://github.com/green-api/whatsapp-api-webhook-server-golang/blob/master/LICENSE)
[![release](https://img.shields.io/github/v/release/green-api/whatsapp-api-webhook-server-golang)](https://github.com/green-api/whatsapp-api-webhook-server-golang/releases)

[Golang Webhook Server библиотека](https://github.com/green-api/whatsapp-api-webhook-server-golang) для интеграции с
мессенджером WhatsApp через API сервиса [green-api.com](https://green-api.com/). Чтобы воспользоваться библиотекой,
нужно получить регистрационный токен и ID аккаунта в [личном кабинете](https://console.green-api.com/). Есть бесплатный
тариф аккаунта разработчика.

#### API

Документация к REST API находится по [ссылке](https://green-api.com/docs/api/). Библиотека является оберткой к REST API,
поэтому документация по ссылке выше применима и к самой библиотеке.

#### Авторизация

Чтобы отправить сообщение или выполнить другие методы Green API, аккаунт WhatsApp в приложении телефона должен быть в
авторизованном состоянии. Для авторизации аккаунта перейдите в [личный кабинет](https://console.green-api.com/) и
сканируйте QR-код с использованием приложения WhatsApp.

#### Примеры подготовки среды

- [Пример подготовки среды для Ubuntu Server](ubuntu.md)

#### [Как запустить веб-сервер](launch.md)

#### Документация по методам сервиса

[Документация по методам сервиса](https://green-api.com/docs/api/)

#### Лицензия

Лицензировано на условиях MIT. Смотрите файл [LICENSE](
https://github.com/green-api/whatsapp-api-webhook-server-golang/blob/master/LICENSE
).
