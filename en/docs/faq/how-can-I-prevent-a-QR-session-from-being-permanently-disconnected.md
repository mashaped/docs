# Как предотвратить постоянное отключение QR-сессии?

Если Ваш инстанс в статусе "Не авторизован", необходимо выполнить команду [reboot](../api/account/Reboot.md), если статус не изменился, требуется отсканировать QR-код в [личном кабинете](https://console.green-api.com).

При сканировании QR-кода создается сессия, которую можно наблюдать в настройках приложения WhatsApp - закладка "Связанные устройства".

В некоторых случаях WhatsApp может произвольно отключать сессию.

Отключение сессии может быть спровоцировано рядом факторов. В первую очередь отключение сессии свидетельствует о том, что WhatsApp заподозрил ваш аккаунт в спаммерской, нежелательной активности.

В этом случает WhatsApp отключает сессию. Если продолжать использовать аккаунт в том же режиме, то следующим шагом со стороны WhatsApp будет блокировка вашего номера.

Таким образом отключение QR-сессии на вашем телефоне может свидетельствовать о приближающемся бане номера, поэтому следует снизить нагрузку на номер.

Факторы, которые повышают риск отключения сессии и блокировки аккаунта:

* использование эмуляторов телефонов вместо физических трубок

* повышенная спаммерская активность

Чтобы снизить риск бана и отключения сессии ознакомьтесь с нашими рекомендациями: [Green API - Как защитить номер от бана?](./how-to-protect-number-from-ban.md)