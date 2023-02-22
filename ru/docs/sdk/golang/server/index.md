# Golang Webhook Server Library

[![license](https://img.shields.io/github/license/green-api/whatsapp-api-webhook-server-golang)](https://github.com/green-api/whatsapp-api-webhook-server-golang/blob/master/LICENSE)
[![release](https://img.shields.io/github/v/release/green-api/whatsapp-api-webhook-server-golang)](https://github.com/green-api/whatsapp-api-webhook-server-golang/releases)

[Golang Webhook Server библиотека](https://github.com/green-api/whatsapp-api-webhook-server-golang) для интеграции с
мессенджером WhatsApp через API сервиса [green-api.com](https://green-api.com/). Чтобы воспользоваться библиотекой,
нужно получить регистрационный токен и ID аккаунта в [личном кабинете](https://console.green-api.com/). Есть бесплатный
тариф аккаунта разработчика.

#### Авторизация

Чтобы отправить сообщение или выполнить другие методы Green API, аккаунт WhatsApp в приложении телефона должен быть в
авторизованном состоянии. Для авторизации аккаунта перейдите в [личный кабинет](https://console.green-api.com/) и
сканируйте QR-код с использованием приложения WhatsApp.

#### Настройки инстанса

Перед началом работы, нужно обновить настройки инстанса в [личном кабинете](https://console.green-api.com/).

- Установите адрес отправки уведомлений (URL)
- Установите заголовок авторизации для отправки уведомлений (опционально)
- Сохраните установленные настройки
- Запустите веб-сервер в консоли
- Отправьте любое сообщение в WhatsApp, например, самому себе

Если вы верно настроили веб-сервер и инстанс, то в консоли будут показаны новые входящие уведомления.

#### Подготовка среды

- [Пример подготовки среды на Ubuntu Server](ubuntu.md)

#### Установка и запуск

- [Пример установки и запуска кода на Ubuntu Server](install.md)

#### Лицензия

Лицензия MIT. [LICENSE](https://github.com/green-api/whatsapp-api-webhook-server-golang/blob/master/LICENSE)
