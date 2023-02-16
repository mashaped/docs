# How to display company name and logo in chats?

Для отображения названия компании в чате рекомендуем воспользоваться следующими способами:

- Отправлять контакт клиенту с использованием метода [SendContact](../api/sending/SendContact.md). После добавление номера в контакты клиент увидит название компании.

- Создать группу, указав в названии группы наименование своей компании, методом [CreateGroup](../api/groups/CreateGroup.md), установить логотип методом [SetGroupPicture](../api/groups/SetGroupPicture.md),  добавить в нее участников с помощью метода [AddGroupParticipant](../api/groups/AddGroupParticipant.md), отправить в группу сообщение методом [SendMessage](../api/sending/SendMessage.md).
