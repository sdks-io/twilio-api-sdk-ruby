# Conversations V1 Webhook

```ruby
conversations_v1_webhook_api = client.conversations_v1_webhook
```

## Class Name

`ConversationsV1WebhookApi`

## Methods

* [Fetch Configuration Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-configuration-webhook)
* [Update Configuration Webhook](../../doc/controllers/conversations-v1-webhook.md#update-configuration-webhook)
* [List Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#list-conversation-scoped-webhook)
* [Create Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#create-conversation-scoped-webhook)
* [Fetch Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-conversation-scoped-webhook)
* [Update Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#update-conversation-scoped-webhook)
* [Delete Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#delete-conversation-scoped-webhook)
* [Create Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#create-service-conversation-scoped-webhook)
* [List Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#list-service-conversation-scoped-webhook)
* [Update Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#update-service-conversation-scoped-webhook)
* [Delete Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#delete-service-conversation-scoped-webhook)
* [Fetch Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-service-conversation-scoped-webhook)
* [Update Service Webhook Configuration](../../doc/controllers/conversations-v1-webhook.md#update-service-webhook-configuration)
* [Fetch Service Webhook Configuration](../../doc/controllers/conversations-v1-webhook.md#fetch-service-webhook-configuration)


# Fetch Configuration Webhook

A Webhook resource manages a service-level set of callback URLs and their configuration for receiving all conversation events.

```ruby
def fetch_configuration_webhook
```

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConfigurationWebhook`](../../doc/models/configuration-webhook.md).

## Example Usage

```ruby
result = conversations_v1_webhook_api.fetch_configuration_webhook

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://example.com/pre",
  "post_webhook_url": "https://example.com/post",
  "method": "GET",
  "filters": [
    "onMessageSend",
    "onConversationUpdated"
  ],
  "target": "webhook",
  "url": "https://conversations.twilio.com/v1/Configuration/Webhooks"
}
```


# Update Configuration Webhook

A Webhook resource manages a service-level set of callback URLs and their configuration for receiving all conversation events.

```ruby
def update_configuration_webhook(method: nil,
                                 filters: nil,
                                 pre_webhook_url: nil,
                                 post_webhook_url: nil,
                                 target: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `method` | `String` | Form, Optional | The HTTP method to be used when sending a webhook request. |
| `filters` | `Array[String]` | Form, Optional | The list of webhook event triggers that are enabled for this Service: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onMessageAdd`, `onMessageUpdate`, `onMessageRemove`, `onConversationUpdated`, `onConversationRemoved`, `onConversationAdd`, `onConversationAdded`, `onConversationRemove`, `onConversationUpdate`, `onConversationStateUpdated`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onParticipantAdd`, `onParticipantRemove`, `onParticipantUpdate`, `onDeliveryUpdated`, `onUserAdded`, `onUserUpdate`, `onUserUpdated` |
| `pre_webhook_url` | `String` | Form, Optional | The absolute url the pre-event webhook request should be sent to. |
| `post_webhook_url` | `String` | Form, Optional | The absolute url the post-event webhook request should be sent to. |
| `target` | [`ConfigurationWebhookTarget`](../../doc/models/configuration-webhook-target.md) | Form, Optional | The routing target of the webhook. Can be ordinary or route internally to Flex |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConfigurationWebhook`](../../doc/models/configuration-webhook.md).

## Example Usage

```ruby
method = 'GET'

filters = [
  'onConversationUpdated'
]

pre_webhook_url = 'https://example.com/pre'

post_webhook_url = 'https://example.com/post'

target = ConfigurationWebhookTarget::WEBHOOK

result = conversations_v1_webhook_api.update_configuration_webhook(
  method: method,
  filters: filters,
  pre_webhook_url: pre_webhook_url,
  post_webhook_url: post_webhook_url,
  target: target
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://example.com/pre",
  "post_webhook_url": "http://example.com/post",
  "method": "GET",
  "filters": [
    "onConversationUpdated"
  ],
  "target": "webhook",
  "url": "https://conversations.twilio.com/v1/Configuration/Webhooks"
}
```


# List Conversation Scoped Webhook

Retrieve a list of all webhooks scoped to the conversation

```ruby
def list_conversation_scoped_webhook(conversation_sid,
                                     page_size: nil,
                                     page: nil,
                                     page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 5, and the maximum is 5.<br><br>**Constraints**: `>= 1`, `<= 5` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListConversationScopedWebhookResponse`](../../doc/models/list-conversation-scoped-webhook-response.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

result = conversations_v1_webhook_api.list_conversation_scoped_webhook(conversation_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Create Conversation Scoped Webhook

Create a new webhook scoped to the conversation

```ruby
def create_conversation_scoped_webhook(conversation_sid,
                                       target,
                                       configuration_url: nil,
                                       configuration_method: nil,
                                       configuration_filters: nil,
                                       configuration_triggers: nil,
                                       configuration_flow_sid: nil,
                                       configuration_replay_after: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `target` | [`ConversationScopedWebhookTarget`](../../doc/models/conversation-scoped-webhook-target.md) | Form, Required | The target of this webhook: `webhook`, `studio`, `trigger` |
| `configuration_url` | `String` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configuration_method` | [`ConversationScopedWebhookMethod`](../../doc/models/conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configuration_filters` | `Array[String]` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configuration_triggers` | `Array[String]` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configuration_flow_sid` | `String` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `configuration_replay_after` | `Integer` | Form, Optional | The message index for which and it's successors the webhook will be replayed. Not set by default |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationScopedWebhook`](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

target = ConversationScopedWebhookTarget::WEBHOOK

configuration_url = 'https://example.com'

configuration_method = ConversationScopedWebhookMethod::GET

configuration_filters = [
  'onMessageSent',
  'onConversationDestroyed'
]

configuration_replay_after = 7

result = conversations_v1_webhook_api.create_conversation_scoped_webhook(
  conversation_sid,
  target,
  configuration_url: configuration_url,
  configuration_method: configuration_method,
  configuration_filters: configuration_filters,
  configuration_replay_after: configuration_replay_after
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Conversation Scoped Webhook

Fetch the configuration of a conversation-scoped webhook

```ruby
def fetch_conversation_scoped_webhook(conversation_sid,
                                      sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationScopedWebhook`](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_webhook_api.fetch_conversation_scoped_webhook(
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Conversation Scoped Webhook

Update an existing conversation-scoped webhook

```ruby
def update_conversation_scoped_webhook(conversation_sid,
                                       sid,
                                       configuration_url: nil,
                                       configuration_method: nil,
                                       configuration_filters: nil,
                                       configuration_triggers: nil,
                                       configuration_flow_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |
| `configuration_url` | `String` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configuration_method` | [`ConversationScopedWebhookMethod`](../../doc/models/conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configuration_filters` | `Array[String]` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configuration_triggers` | `Array[String]` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configuration_flow_sid` | `String` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationScopedWebhook`](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

configuration_url = 'https://example.com'

configuration_method = ConversationScopedWebhookMethod::POST

configuration_triggers = [
  'keyword1',
  'keyword2'
]

result = conversations_v1_webhook_api.update_conversation_scoped_webhook(
  conversation_sid,
  sid,
  configuration_url: configuration_url,
  configuration_method: configuration_method,
  configuration_triggers: configuration_triggers
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Conversation Scoped Webhook

Remove an existing webhook scoped to the conversation

```ruby
def delete_conversation_scoped_webhook(conversation_sid,
                                       sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_webhook_api.delete_conversation_scoped_webhook(
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Create Service Conversation Scoped Webhook

Create a new webhook scoped to the conversation in a specific service

```ruby
def create_service_conversation_scoped_webhook(chat_service_sid,
                                               conversation_sid,
                                               target,
                                               configuration_url: nil,
                                               configuration_method: nil,
                                               configuration_filters: nil,
                                               configuration_triggers: nil,
                                               configuration_flow_sid: nil,
                                               configuration_replay_after: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `target` | [`ServiceConversationScopedWebhookTarget`](../../doc/models/service-conversation-scoped-webhook-target.md) | Form, Required | The target of this webhook: `webhook`, `studio`, `trigger` |
| `configuration_url` | `String` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configuration_method` | [`ServiceConversationScopedWebhookMethod`](../../doc/models/service-conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configuration_filters` | `Array[String]` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configuration_triggers` | `Array[String]` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configuration_flow_sid` | `String` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `configuration_replay_after` | `Integer` | Form, Optional | The message index for which and it's successors the webhook will be replayed. Not set by default |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationScopedWebhook`](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

target = ServiceConversationScopedWebhookTarget::WEBHOOK

configuration_url = 'https://example.com'

configuration_method = ServiceConversationScopedWebhookMethod::GET

configuration_filters = [
  'onMessageSent',
  'onConversationDestroyed'
]

configuration_replay_after = 7

result = conversations_v1_webhook_api.create_service_conversation_scoped_webhook(
  chat_service_sid,
  conversation_sid,
  target,
  configuration_url: configuration_url,
  configuration_method: configuration_method,
  configuration_filters: configuration_filters,
  configuration_replay_after: configuration_replay_after
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Service Conversation Scoped Webhook

Retrieve a list of all webhooks scoped to the conversation

```ruby
def list_service_conversation_scoped_webhook(chat_service_sid,
                                             conversation_sid,
                                             page_size: nil,
                                             page: nil,
                                             page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 5, and the maximum is 5.<br><br>**Constraints**: `>= 1`, `<= 5` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListServiceConversationScopedWebhookResponse`](../../doc/models/list-service-conversation-scoped-webhook-response.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

result = conversations_v1_webhook_api.list_service_conversation_scoped_webhook(
  chat_service_sid,
  conversation_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Service Conversation Scoped Webhook

Update an existing conversation-scoped webhook

```ruby
def update_service_conversation_scoped_webhook(chat_service_sid,
                                               conversation_sid,
                                               sid,
                                               configuration_url: nil,
                                               configuration_method: nil,
                                               configuration_filters: nil,
                                               configuration_triggers: nil,
                                               configuration_flow_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |
| `configuration_url` | `String` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configuration_method` | [`ServiceConversationScopedWebhookMethod`](../../doc/models/service-conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configuration_filters` | `Array[String]` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configuration_triggers` | `Array[String]` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configuration_flow_sid` | `String` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationScopedWebhook`](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

configuration_url = 'https://example.com'

configuration_method = ServiceConversationScopedWebhookMethod::POST

configuration_triggers = [
  'keyword1',
  'keyword2'
]

result = conversations_v1_webhook_api.update_service_conversation_scoped_webhook(
  chat_service_sid,
  conversation_sid,
  sid,
  configuration_url: configuration_url,
  configuration_method: configuration_method,
  configuration_triggers: configuration_triggers
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Service Conversation Scoped Webhook

Remove an existing webhook scoped to the conversation

```ruby
def delete_service_conversation_scoped_webhook(chat_service_sid,
                                               conversation_sid,
                                               sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_webhook_api.delete_service_conversation_scoped_webhook(
  chat_service_sid,
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Service Conversation Scoped Webhook

Fetch the configuration of a conversation-scoped webhook

```ruby
def fetch_service_conversation_scoped_webhook(chat_service_sid,
                                              conversation_sid,
                                              sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationScopedWebhook`](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_webhook_api.fetch_service_conversation_scoped_webhook(
  chat_service_sid,
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Service Webhook Configuration

Update a specific Webhook.

```ruby
def update_service_webhook_configuration(chat_service_sid,
                                         pre_webhook_url: nil,
                                         post_webhook_url: nil,
                                         filters: nil,
                                         method: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `pre_webhook_url` | `String` | Form, Optional | The absolute url the pre-event webhook request should be sent to. |
| `post_webhook_url` | `String` | Form, Optional | The absolute url the post-event webhook request should be sent to. |
| `filters` | `Array[String]` | Form, Optional | The list of events that your configured webhook targets will receive. Events not configured here will not fire. Possible values are `onParticipantAdd`, `onParticipantAdded`, `onDeliveryUpdated`, `onConversationUpdated`, `onConversationRemove`, `onParticipantRemove`, `onConversationUpdate`, `onMessageAdd`, `onMessageRemoved`, `onParticipantUpdated`, `onConversationAdded`, `onMessageAdded`, `onConversationAdd`, `onConversationRemoved`, `onParticipantUpdate`, `onMessageRemove`, `onMessageUpdated`, `onParticipantRemoved`, `onMessageUpdate` or `onConversationStateUpdated`. |
| `method` | `String` | Form, Optional | The HTTP method to be used when sending a webhook request. One of `GET` or `POST`. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceWebhookConfiguration`](../../doc/models/service-webhook-configuration.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

pre_webhook_url = 'https://www.example.com/pre'

post_webhook_url = 'https://www.example.com/post'

filters = [
  'onMessageRemoved',
  'onParticipantAdded'
]

method = 'GET'

result = conversations_v1_webhook_api.update_service_webhook_configuration(
  chat_service_sid,
  pre_webhook_url: pre_webhook_url,
  post_webhook_url: post_webhook_url,
  filters: filters,
  method: method
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://www.example.com/pre",
  "post_webhook_url": "https://www.example.com/post",
  "filters": [
    "onMessageRemoved",
    "onParticipantAdded"
  ],
  "method": "GET",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
}
```


# Fetch Service Webhook Configuration

Fetch a specific service webhook configuration.

```ruby
def fetch_service_webhook_configuration(chat_service_sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceWebhookConfiguration`](../../doc/models/service-webhook-configuration.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

result = conversations_v1_webhook_api.fetch_service_webhook_configuration(chat_service_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://www.example.com/pre",
  "post_webhook_url": "https://www.example.com/post",
  "filters": [
    "onMessageRemove",
    "onParticipantAdd"
  ],
  "method": "POST",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
}
```

