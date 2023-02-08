# Rate limiter

The system is designed to prevent incorrect use of the API.
Requests made with a frequency higher than indicated in the table will be rejected with error 429.

| Method          | Requests per second |                    
| --------------- | :-----------------: |
|getSettings| 1|
|setSettings| 1|
|getStateInstance| 1|
|getStatusInstance| 1|
|reboot| 1|
|logout| 1|
|qr| 3|
|scanQrCode| 1|
|setProfilePicture| 1|
|sendFileByUpload| 5|
|receiveNotification| 100|
|deleteNotification| 100|
|downloadFile| 5|
|getChatHistory| 1|
|getMessage| 10|
|lastIncomingMessages| 1|
|lastOutgoingMessages| 1|
|createGroup| 1|
|updateGroupName| 1|
|getGroupData| 1|
|addGroupParticipant| 10|
|removeGroupParticipant| 10|
|setGroupAdmin| 10|
|removeAdmin| 10|
|setGroupPicture| 1|
|leaveGroup| 10|
|readChat| 10|
|getDeviceInfo| 1|
|checkWhatsapp| 10|
|getAvatar| 10|
|getAvatarAsync| 10|
|getContacts| 1|
|getContactInfo| 1|
|deleteMessage| 10|
|archiveChat| 10|
|unarchiveChat| 10|
|setDisappearingChat| 1|
|getWaSettings| 1|
|getChats| 1|
|sendMessage| 50|
|sendButtons| 50|
|sendTemplateButtons| 50|
|sendListMessage| 50|
|sendLocation| 50|
|sendLink| 50|
|sendContact| 50|
|sendFileByUrl| 50|
|clearMessagesQueue| 1|
|showMessagesQueue| 1|
|sendTemplate| 50|
|forwardMessages| 50|