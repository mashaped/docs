# ForwardMessages

O método destina-se ao encaminhamento de mensagens para um bate-papo pessoal ou em grupo.
As mensagens encaminhadas serão adicionadas à fila de envio. A verificação da autorização do whatsapp no telefone (ou seja, disponibilidade em dispositivos vinculados) não é realizada. A mensagem será mantida por 24 horas na fila e será enviada imediatamente após a autorização do telefone.
A mensagem será adicionada à fila de envio. A velocidade do envio de mensagens da fila é controlada pelo parâmetro [Intervalo de envio de mensagens](../send-messages-delay.md).

## Solicitação {#request}

Para encaminhamento, você precisa fazer uma solicitação para:
```
POST https://api.green-api.com/waInstance{{idInstance}}/forwardMessages/{{apiTokenInstance}}
```

Para obter os parâmetros de requisição `idInstance` e` apiTokenInstance`, consulte a seção [Antes de começar](../../before-start.md#parameters).

### Parâmetros para requisição {#request-parameters}

| Parâmetro    | Tipo              | Obrigatório | Descrição                                                                       |
|--------------|-------------------|-------------|---------------------------------------------------------------------------------|
| `chatId`     | **string**        | Sim         | [ID Do Chat](../chat-id.md), a partir do qual a mensagem está sendo encaminhada |
| `chatIdFrom` | **string**        | Sim         | [ID Do Chat](../chat-id.md), para onde a mensagem é encaminhada                 |
| `messages`   | **array<string>** | Sim         | Coleta de IDs de mensagens encaminhadas                                         |

### Exemplo de uma requisição {#request-example-body}

Encaminhando uma mensagem para um bate-papo:
```json
{
    "chatId": "11001234567@c.us",
    "chatIdFrom": "11001234567@c.us",
    "messages": [
       "BAE587FA1CECF760",
       "BAE5608BC86F2B59"
    ]
}
```

## Resposta {#response}

### Parâmetros de Resposta {#response-parameters}

| Parâmetro  | Tipo              | Descrição          |
|------------|-------------------|----------------------|
| `messages` | **array<string>** | Ids das mensagens enviadas |

### Exemplo de uma resposta {#response-example-body}

```json
{
  "messages": [
    "BAE5DBB8DEABDA22",
    "BAE5BBA9BE3142D8"
  ]
}
```
### Exemplo de exibição do destinatário {#recieve-example}

![Exemplo de uma mensagem encaminhada](../../assets/forward-message.jpg 'Exemplo de uma mensagem encaminhada')

### Encaminhar erros de mensagens {#errors}

Para obter uma lista dos métodos de erro comuns para todos os métodos, consulte [Erros mais Comuns](../common-errors.md)

## curl example

```
curl --location --request POST 'https://api.green-api.com/waInstance{{idInstance}}/forwardMessages/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "11001234567@c.us",
    "chatIdFrom": "11001234567@c.us",
    "messages": [
        "BAE587FA1CECF760",
        "BAE5608BC86F2B59"
    ]
}'
```