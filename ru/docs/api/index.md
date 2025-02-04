# Документация API

Green API предоставляет HTTP API WhatsApp для отправки и получения сообщений, файлов, работы с групповыми чатами, получения списка контактов и других методов.

Перед выполнением запросов убедитесь, что выполнены все шаги раздела [Перед началом работы](../before-start.md). Ознакомьтесь с разделом [Выполнение запросов](../request-format.md). Для отладки запросов к Green API воспользуйтесь [Коллекцией Postman](../postman-collection.md).

## [Аккаунт](./account/index.md) {#account}

- [Получить настройки аккаунта](./account/GetSettings.md)
- [Установить настройки аккаунта](./account/SetSettings.md)
- [Получить состояние аккаунта](./account/GetStateInstance.md)
- [Перезапустить аккаунт](./account/Reboot.md)
- [Разлогинить аккаунт](./account/Logout.md)
- [Получить QR-код](./account/QR.md)
- [Получить QR-код через websocket](./account/Scanqrcode.md)

## [Отправка](./sending/index.md) {#sending}

- [Отправить текст](./sending/SendMessage.md)
- [Отправить обычные кнопки](./sending/SendButtons.md)
- [Отправить шаблонные кнопки](./sending/SendTemplateButtons.md)
- [Отправить список выбора](./sending/SendListMessage.md)
- [Отправить видео, аудио, изображение, документ](./sending/SendFileByUpload.md)
- [Отправить видео, аудио, изображение, документ по URL](./sending/SendFileByUrl.md)
- [Отправить геолокацию](./sending/SendLocation.md)
- [Отправить контакт](./sending/SendContact.md)
- [Отправить ссылку](./sending/SendLink.md)
- [Переслать сообщения](./sending/ForwardMessages.md)

## [Получение](./receiving/index.md) {#receiving}

### [Получение уведомлений через HTTP API](receiving/technology-http-api.md) {#technology-http-api}
- [Получить уведомление](receiving/technology-http-api/ReceiveNotification.md)
- [Удалить уведомление](receiving/technology-http-api/DeleteNotification.md)

### [Получение уведомлений через Webhook Endpoint](receiving/technology-webhook-endpoint.md) {#technology-webhook-endpoint}

### [Формат входящих уведомлений](receiving/notifications-format/index.md) {#notifications-format}

#### [Входящее сообщение](receiving/notifications-format/incoming-message/Webhook-IncomingMessageReceived.md) {#receiving-incoming-message}

- [Входящее текстовое сообщение](./receiving/notifications-format/incoming-message/TextMessage.md)
- [Выбор обычной кнопки](./receiving/notifications-format/selected-buttons/ButtonsResponseMessage.md)
- [Выбор шаблонной кнопки](./receiving/notifications-format/selected-buttons/TemplateButtonsReplyMessage.md)
- [Выбор элемента списка](./receiving/notifications-format/selected-buttons/ListResponseMessage.md)
- [Входящее текстовое сообщение, сообщение с URL, рекламное сообщение](./receiving/notifications-format/incoming-message/ExtendedTextMessage.md)
- [Входящее сообщение с изображением, видео, аудио, документом](./receiving/notifications-format/incoming-message/ImageMessage.md)
- [Входящее сообщение с геолокацией](./receiving/notifications-format/incoming-message/LocationMessage.md)
- [Входящее сообщение с контактом](./receiving/notifications-format/incoming-message/ContactMessage.md)
- [Входящее сообщение с массивом контактов](./receiving/notifications-format/incoming-message/ContactsArrayMessage.md)
- [Входящее сообщение со стикером](./receiving/notifications-format/incoming-message/StickerMessage.md)
- [Входящее сообщение-реакция](./receiving/notifications-format/incoming-message/ReactionMessage.md)
- [Входящее сообщение с приглашением в группу](./receiving/notifications-format/incoming-message/GroupInviteMessage.md)
- [Входящее сообщение с опросом](./receiving/notifications-format/incoming-message/PollMessage.md)

#### Отправленное сообщение {#receiving-outgoing-message}

- [Отправленное с телефона сообщение](./receiving/notifications-format/outgoing-message/OutgoingMessage.md)
- [Отправленное сообщение через API](./receiving/notifications-format/outgoing-message/OutgoingApiMessage.md)
- [Статус отправленного сообщения](./receiving/notifications-format/outgoing-message/OutgoingMessageStatus.md)

#### Прочие {#receiving-dif}

- [Статус аккаунта](./receiving/notifications-format/StateInstanceChanged.md)
- [Статус устройства](./receiving/notifications-format/DeviceInfo.md)
- [Входящий звонок](./receiving/notifications-format/IncomingCall.md)

#### Объекты {#receiving-obj}

- [Типы входящих уведомлений](./receiving/notifications-format/type-webhook.md)

### Получение файлов {#receiving-files}

- [Скачать файл из входящего сообщения](./receiving/files/DownloadFile.md)


## [Журналы](./journals/index.md) {#journals}

- [Получить историю сообщений чата](./journals/GetChatHistory.md)
- [Получить сообщение чата](./journals/GetMessage.md)
- [Получить журнал входящих сообщений](./journals/LastIncomingMessages.md)
- [Получить журнал отправленных сообщений](./journals/LastOutgoingMessages.md)

## [Очереди](./queues/index.md) {#queues}

- [Получить очередь сообщений к отправке](./queues/ShowMessagesQueue.md)
- [Очистить очередь сообщений к отправке](./queues/ClearMessagesQueue.md)

## [Группы](./groups/index.md) {#groups}

- [Создать группу](./groups/CreateGroup.md)
- [Изменить имя группы](./groups/UpdateGroupName.md)
- [Получить информацию о группе](./groups/GetGroupData.md)
- [Добавить участника в группу](./groups/AddGroupParticipant.md)
- [Удалить участника из группы](./groups/RemoveGroupParticipant.md)
- [Назначить права администратора группы](./groups/SetGroupAdmin.md)
- [Отозвать права администратора группы](./groups/RemoveAdmin.md)
- [Выйти из группы](./groups/LeaveGroup.md)

## [Отметка прочтения](./marks/index.md) {#marks}

- [Отметить чат прочитанным](./marks/ReadChat.md)

## [Устройство (телефон)](./phone/index.md) {#phone}

- [Получить информацию об устройстве](./phone/GetDeviceInfo.md)

## [Сервисные методы](./service/index.md) {#service}

- [Проверить наличие WhatsApp](./service/CheckWhatsapp.md)
- [Получить аватар](./service/GetAvatar.md)
- [Получить аватар асинхронно](./service/GetAvatarAsync.md)
- [Получить контакты](./service/GetContacts.md)
- [Получить информацию о контакте](./service/GetContactInfo.md)
- [Удалить сообщение](./service/deleteMessage.md)
- [Архивировать чат](./service/archiveChat.md)
- [Разархивировать чат](./service/unarchiveChat.md)
- [Изменить настройки исчезающих сообщений чата](./service/SetDisappearingChat.md)

## Прочее {#dif}

- [Идентификатор чата](chat-id.md)
- [Интервал отправки сообщений](send-messages-delay.md)
- [Стандартные ошибки](common-errors.md)
