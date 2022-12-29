# Golang WhatsApp Library

[![license](https://img.shields.io/github/license/green-api/whatsapp-api-client-golang)](https://github.com/green-api/whatsapp-api-client-golang/blob/master/LICENSE)
[![release](https://img.shields.io/github/v/release/green-api/whatsapp-api-client-golang)](https://github.com/green-api/whatsapp-api-client-golang/releases)

[Golang WhatsApp Library](https://github.com/green-api/whatsapp-api-client-golang) - Go library designed to integrate
with WhatsApp using the service [GREEN API](https://green-api.com/). To start using the library, you need to get an ID
and a token account in [personal cabinet](https://console.green-api.com/).

#### API

The documentation for the REST API can be found [here](https://green-api.com/docs/api/). The library is a wrapper for
the REST API, so the documentation at the link above applies to the library itself.

#### Authorization

To send a message or perform other API methods, the WhatsApp account in the phone app should be in authorized state. To
authorize the account, you need to scan the QR code in [personal account](https://console.green-api.com/) using the
WhatsApp application.

#### [How to create a group](create_group.md)

#### [How to send a message](send_message.md)

#### [How to send a message with an attachment](send_file_by_upload.md)

#### [List of all library methods](all_methods.md)

### License

MIT License. [LICENSE](https://github.com/green-api/whatsapp-api-client-golang/blob/main/LICENSE)
