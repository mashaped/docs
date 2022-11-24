# 1C WhatsApp processing model

[1C processing model](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf) for integration of 1С with WhatsAPP messenger via API of [green-api.com](https://green-api.com) service. You can also use [configuration sources in xml download format](https://github.com/green-api/whatsapp-api-client-1c). To use the library you have to get a registration token and an account id in the [personal area](https://console.green-api.com). There is a free developer account tariff plan.

#### Download a processing model

Обработку можно скачать здесь [![Скачать](../../assets/button_download.svg)](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf)

После запуска обработки в 1С потребуется ввести идентификатор инстанса и токен авторизации

![`Скриншот`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Screenshort.png?raw=true)

#### Требования
Платформа 1С не ниже версии 8.3.10

#### API

You can find REST API documentation by [url](https://green-api.com/docs/api/). The library is a wrapper for REST API, so the documentation at the above url applies to the library as well.

#### Authorization

To send a message or to execute some other Green-API method, you have to have the WhatsApp account in the phone application to be authorized. To authorize your account please go to the [personal area](https://console.green-api.com) and scan a QR-code using the WhatsApp application.

#### [How to send a text message](sendmessage.md)
#### [How to send a text message to a group](sendmessagegroup.md)
#### [How to receive a message](receivenotification.md)

#### Service methods documentation

[Service methods documentation](https://green-api.com/docs/api/)

#### Установка обработки из исходников

Исходники в репозитории - это xml выгрузка из конфигуратора 1С версии 8.3.16 в режиме совместимости с 8.3.10. Скачайте исходники с репозитория и загрузите в конфигуратор с помощью команды Конфигурация -> Загрузить конфигурацию из файлов

#### License

Licensed under MIT terms. Please see file [LICENSE](https://github.com/green-api/whatsapp-api-client-1c/blob/master/LICENSE)
