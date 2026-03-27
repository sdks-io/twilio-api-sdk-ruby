# Conversations V1 Message

```ruby
conversations_v1_message_api = client.conversations_v1_message
```

## Class Name

`ConversationsV1MessageApi`

## Methods

* [Create Conversation Message](../../doc/controllers/conversations-v1-message.md#create-conversation-message)
* [List Conversation Message](../../doc/controllers/conversations-v1-message.md#list-conversation-message)
* [Update Conversation Message](../../doc/controllers/conversations-v1-message.md#update-conversation-message)
* [Delete Conversation Message](../../doc/controllers/conversations-v1-message.md#delete-conversation-message)
* [Fetch Conversation Message](../../doc/controllers/conversations-v1-message.md#fetch-conversation-message)
* [Create Service Conversation Message](../../doc/controllers/conversations-v1-message.md#create-service-conversation-message)
* [List Service Conversation Message](../../doc/controllers/conversations-v1-message.md#list-service-conversation-message)
* [Update Service Conversation Message](../../doc/controllers/conversations-v1-message.md#update-service-conversation-message)
* [Delete Service Conversation Message](../../doc/controllers/conversations-v1-message.md#delete-service-conversation-message)
* [Fetch Service Conversation Message](../../doc/controllers/conversations-v1-message.md#fetch-service-conversation-message)


# Create Conversation Message

Add a new message to the conversation

```ruby
def create_conversation_message(conversation_sid,
                                x_twilio_webhook_enabled: nil,
                                author: nil,
                                body: nil,
                                date_created: nil,
                                date_updated: nil,
                                attributes: nil,
                                media_sid: nil,
                                content_sid: nil,
                                content_variables: nil,
                                subject: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `String` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `String` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `String` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `media_sid` | `String` | Form, Optional | The Media SID to be attached to the new Message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^ME[0-9a-fA-F]{32}$` |
| `content_sid` | `String` | Form, Optional | The unique ID of the multi-channel [Rich Content](https://www.twilio.com/docs/content) template, required for template-generated messages.  **Note** that if this field is set, `Body` and `MediaSid` parameters are ignored.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |
| `content_variables` | `String` | Form, Optional | A structurally valid JSON string that contains values to resolve Rich Content template variables. |
| `subject` | `String` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationMessage`](../../doc/models/conversation-message.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

author = 'message author'

body = 'Hello'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "importance": "high" }'

media_sid = 'MEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

content_sid = 'HXaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

content_variables = '{"name": "John"}'

subject = 'message subject'

result = conversations_v1_message_api.create_conversation_message(
  conversation_sid,
  author: author,
  body: body,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  media_sid: media_sid,
  content_sid: content_sid,
  content_variables: content_variables,
  subject: subject
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Conversation Message

Retrieve a list of all messages in the conversation

```ruby
def list_conversation_message(conversation_sid,
                              order: nil,
                              page_size: nil,
                              page: nil,
                              page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for messages. |
| `order` | [`ConversationMessageOrderType`](../../doc/models/conversation-message-order-type.md) | Query, Optional | The sort order of the returned messages. Can be: `asc` (ascending) or `desc` (descending), with `asc` as the default. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListConversationMessageResponse`](../../doc/models/list-conversation-message-response.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

order = ConversationMessageOrderType::DESC

result = conversations_v1_message_api.list_conversation_message(
  conversation_sid,
  order: order
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Conversation Message

Update an existing message in the conversation

```ruby
def update_conversation_message(conversation_sid,
                                sid,
                                x_twilio_webhook_enabled: nil,
                                author: nil,
                                body: nil,
                                date_created: nil,
                                date_updated: nil,
                                attributes: nil,
                                subject: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `String` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `String` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `String` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `subject` | `String` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationMessage`](../../doc/models/conversation-message.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

author = 'message author'

body = 'Hello'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "importance": "high" }'

result = conversations_v1_message_api.update_conversation_message(
  conversation_sid,
  sid,
  author: author,
  body: body,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Conversation Message

Remove a message from the conversation

```ruby
def delete_conversation_message(conversation_sid,
                                sid,
                                x_twilio_webhook_enabled: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_message_api.delete_conversation_message(
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Conversation Message

Fetch a message from the conversation

```ruby
def fetch_conversation_message(conversation_sid,
                               sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationMessage`](../../doc/models/conversation-message.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_message_api.fetch_conversation_message(
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Create Service Conversation Message

Add a new message to the conversation in a specific service

```ruby
def create_service_conversation_message(chat_service_sid,
                                        conversation_sid,
                                        x_twilio_webhook_enabled: nil,
                                        author: nil,
                                        body: nil,
                                        date_created: nil,
                                        date_updated: nil,
                                        attributes: nil,
                                        media_sid: nil,
                                        content_sid: nil,
                                        content_variables: nil,
                                        subject: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `String` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `String` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `String` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `media_sid` | `String` | Form, Optional | The Media SID to be attached to the new Message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^ME[0-9a-fA-F]{32}$` |
| `content_sid` | `String` | Form, Optional | The unique ID of the multi-channel [Rich Content](https://www.twilio.com/docs/content) template, required for template-generated messages.  **Note** that if this field is set, `Body` and `MediaSid` parameters are ignored.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |
| `content_variables` | `String` | Form, Optional | A structurally valid JSON string that contains values to resolve Rich Content template variables. |
| `subject` | `String` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationMessage`](../../doc/models/service-conversation-message.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

author = 'message author'

body = 'Hello'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "importance": "high" }'

media_sid = 'MEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

content_sid = 'HXaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

content_variables = '{"name": "John"}'

subject = 'message subject'

result = conversations_v1_message_api.create_service_conversation_message(
  chat_service_sid,
  conversation_sid,
  author: author,
  body: body,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  media_sid: media_sid,
  content_sid: content_sid,
  content_variables: content_variables,
  subject: subject
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Service Conversation Message

Retrieve a list of all messages in the conversation

```ruby
def list_service_conversation_message(chat_service_sid,
                                      conversation_sid,
                                      order: nil,
                                      page_size: nil,
                                      page: nil,
                                      page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for messages. |
| `order` | [`ServiceConversationMessageOrderType`](../../doc/models/service-conversation-message-order-type.md) | Query, Optional | The sort order of the returned messages. Can be: `asc` (ascending) or `desc` (descending), with `asc` as the default. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListServiceConversationMessageResponse`](../../doc/models/list-service-conversation-message-response.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

order = ServiceConversationMessageOrderType::DESC

result = conversations_v1_message_api.list_service_conversation_message(
  chat_service_sid,
  conversation_sid,
  order: order
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Service Conversation Message

Update an existing message in the conversation

```ruby
def update_service_conversation_message(chat_service_sid,
                                        conversation_sid,
                                        sid,
                                        x_twilio_webhook_enabled: nil,
                                        author: nil,
                                        body: nil,
                                        date_created: nil,
                                        date_updated: nil,
                                        attributes: nil,
                                        subject: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `String` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `String` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `String` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `subject` | `String` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationMessage`](../../doc/models/service-conversation-message.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

author = 'message author'

body = 'Hello'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "importance": "high" }'

result = conversations_v1_message_api.update_service_conversation_message(
  chat_service_sid,
  conversation_sid,
  sid,
  author: author,
  body: body,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Service Conversation Message

Remove a message from the conversation

```ruby
def delete_service_conversation_message(chat_service_sid,
                                        conversation_sid,
                                        sid,
                                        x_twilio_webhook_enabled: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_message_api.delete_service_conversation_message(
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


# Fetch Service Conversation Message

Fetch a message from the conversation

```ruby
def fetch_service_conversation_message(chat_service_sid,
                                       conversation_sid,
                                       sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationMessage`](../../doc/models/service-conversation-message.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_message_api.fetch_service_conversation_message(
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

