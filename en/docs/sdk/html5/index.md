# HTML5 Js WhatsApp Library
* [![build](https://github.com/green-api/whatsapp-api-client/workflows/build_library/badge.svg)](https://github.com/green-api/whatsapp-api-client/actions/workflows/build_library.yml)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/green-api/whatsapp-api-client/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/green-api/whatsapp-api-client.svg)](https://github.com/green-api/whatsapp-api-client/releases)

[Javascript library](https://github.com/green-api/whatsapp-api-client-js) for integration of HTML with WhatsAPP messenger via API of [green-api.com](https://green-api.com) service. It is a specific case of the [NodeJs WhatsApp Library](../nodejs/index.md) usage. To use the library you have to get a registration token and an account id in the [personal area](https://console.green-api.com). There is a free developer account tariff plan.

#### API

You can find REST API documentation by [url](https://green-api.com/docs/api/). The library is a wrapper for REST API, so the documentation at the above url applies to the library as well.

#### Authorization 

To send a message or to execute some other Green-API method, you have to have the WhatsApp account in the phone application to be authorized. To authorize your account please go to the [personal area](https://console.green-api.com) and scan a QR-code using the WhatsApp application.

#### [How to send a text message from a browser](sendmessage.md)

#### Development enviri=onment unrolling

1. Clone the repository via ``git clone``
2. Install dependencies via ``npm install``
3. Globally install the ``rollup`` library for building.
4. For webhooks add `express` as a new dependency via npm
5. Create an `.env` file in the root directory and set the environment variables. The example of variables are in the [env.example](https://github.com/green-api/whatsapp-api-client-js/blob/master/env.example) file

#### Building
You can compile both browser and node/webpack versions of the library with one command
```
npm run build
```
#### Service methods documentation

[Service methods documentation](https://green-api.com/docs/api/)

#### External products

* [axios](https://github.com/axios/axios) - for http requests
* [express](https://www.npmjs.com/package/express) - webhook applications server

#### License

Licensed under MIT terms. Please see file [LICENSE](https://github.com/green-api/whatsapp-api-client-python/blob/master/LICENSE)
