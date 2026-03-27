# Conversations V1 Conversation

```ruby
conversations_v1_conversation_api = client.conversations_v1_conversation
```

## Class Name

`ConversationsV1ConversationApi`

## Methods

* [Create Conversation](../../doc/controllers/conversations-v1-conversation.md#create-conversation)
* [List Conversation](../../doc/controllers/conversations-v1-conversation.md#list-conversation)
* [Update Conversation](../../doc/controllers/conversations-v1-conversation.md#update-conversation)
* [Delete Conversation](../../doc/controllers/conversations-v1-conversation.md#delete-conversation)
* [Fetch Conversation](../../doc/controllers/conversations-v1-conversation.md#fetch-conversation)
* [Create Service Conversation](../../doc/controllers/conversations-v1-conversation.md#create-service-conversation)
* [List Service Conversation](../../doc/controllers/conversations-v1-conversation.md#list-service-conversation)
* [Update Service Conversation](../../doc/controllers/conversations-v1-conversation.md#update-service-conversation)
* [Delete Service Conversation](../../doc/controllers/conversations-v1-conversation.md#delete-service-conversation)
* [Fetch Service Conversation](../../doc/controllers/conversations-v1-conversation.md#fetch-service-conversation)


# Create Conversation

Create a new conversation in your account's default service

```ruby
def create_conversation(x_twilio_webhook_enabled: nil,
                        friendly_name: nil,
                        unique_name: nil,
                        date_created: nil,
                        date_updated: nil,
                        messaging_service_sid: nil,
                        attributes: nil,
                        state: nil,
                        timers_inactive: nil,
                        timers_closed: nil,
                        bindings_email_address: nil,
                        bindings_email_name: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendly_name` | `String` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `unique_name` | `String` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. |
| `messaging_service_sid` | `String` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `state` | [`ConversationState`](../../doc/models/conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timers_inactive` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timers_closed` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindings_email_address` | `String` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindings_email_name` | `String` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Conversation`](../../doc/models/conversation.md).

## Example Usage

```ruby
friendly_name = 'friendly_name'

unique_name = 'unique_name'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

messaging_service_sid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

attributes = '{ "topic": "feedback" }'

state = ConversationState::INACTIVE

timers_inactive = 'PT1M'

timers_closed = 'PT10M'

result = conversations_v1_conversation_api.create_conversation(
  friendly_name: friendly_name,
  unique_name: unique_name,
  date_created: date_created,
  date_updated: date_updated,
  messaging_service_sid: messaging_service_sid,
  attributes: attributes,
  state: state,
  timers_inactive: timers_inactive,
  timers_closed: timers_closed
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Conversation

Retrieve a list of conversations in your account's default service

```ruby
def list_conversation(start_date: nil,
                      end_date: nil,
                      state: nil,
                      page_size: nil,
                      page: nil,
                      page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `start_date` | `String` | Query, Optional | Specifies the beginning of the date range for filtering Conversations based on their creation date. Conversations that were created on or after this date will be included in the results. The date must be in ISO8601 format, specifically starting at the beginning of the specified date (YYYY-MM-DDT00:00:00Z), for precise filtering. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `end_date` | `String` | Query, Optional | Defines the end of the date range for filtering conversations by their creation date. Only conversations that were created on or before this date will appear in the results.  The date must be in ISO8601 format, specifically capturing up to the end of the specified date (YYYY-MM-DDT23:59:59Z), to ensure that conversations from the entire end day are included. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `state` | [`ConversationState`](../../doc/models/conversation-state.md) | Query, Optional | State for sorting and filtering list of Conversations. Can be `active`, `inactive` or `closed` |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListConversationResponse`](../../doc/models/list-conversation-response.md).

## Example Usage

```ruby
result = conversations_v1_conversation_api.list_conversation

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Conversation

Update an existing conversation in your account's default service

```ruby
def update_conversation(sid,
                        x_twilio_webhook_enabled: nil,
                        friendly_name: nil,
                        date_created: nil,
                        date_updated: nil,
                        attributes: nil,
                        messaging_service_sid: nil,
                        state: nil,
                        timers_inactive: nil,
                        timers_closed: nil,
                        unique_name: nil,
                        bindings_email_address: nil,
                        bindings_email_name: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendly_name` | `String` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messaging_service_sid` | `String` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `state` | [`ConversationState`](../../doc/models/conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timers_inactive` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timers_closed` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `unique_name` | `String` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `bindings_email_address` | `String` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindings_email_name` | `String` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Conversation`](../../doc/models/conversation.md).

## Example Usage

```ruby
sid = 'Sid8'

friendly_name = 'friendly_name'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "topic": "feedback" }'

messaging_service_sid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaab'

state = ConversationState::INACTIVE

timers_inactive = 'PT1M'

timers_closed = 'PT10M'

unique_name = 'unique_name'

result = conversations_v1_conversation_api.update_conversation(
  sid,
  friendly_name: friendly_name,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  messaging_service_sid: messaging_service_sid,
  state: state,
  timers_inactive: timers_inactive,
  timers_closed: timers_closed,
  unique_name: unique_name
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Conversation

Remove a conversation from your account's default service

```ruby
def delete_conversation(sid,
                        x_twilio_webhook_enabled: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
sid = 'Sid8'

result = conversations_v1_conversation_api.delete_conversation(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Conversation

Fetch a conversation from your account's default service

```ruby
def fetch_conversation(sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Conversation`](../../doc/models/conversation.md).

## Example Usage

```ruby
sid = 'Sid8'

result = conversations_v1_conversation_api.fetch_conversation(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Create Service Conversation

Create a new conversation in your service

```ruby
def create_service_conversation(chat_service_sid,
                                x_twilio_webhook_enabled: nil,
                                friendly_name: nil,
                                unique_name: nil,
                                attributes: nil,
                                messaging_service_sid: nil,
                                date_created: nil,
                                date_updated: nil,
                                state: nil,
                                timers_inactive: nil,
                                timers_closed: nil,
                                bindings_email_address: nil,
                                bindings_email_name: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendly_name` | `String` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `unique_name` | `String` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messaging_service_sid` | `String` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. |
| `state` | [`ServiceConversationState`](../../doc/models/service-conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timers_inactive` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timers_closed` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindings_email_address` | `String` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindings_email_name` | `String` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversation`](../../doc/models/service-conversation.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

friendly_name = 'friendly_name'

unique_name = 'unique_name'

attributes = '{ "topic": "feedback" }'

messaging_service_sid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

state = ServiceConversationState::INACTIVE

timers_inactive = 'PT1M'

timers_closed = 'PT10M'

result = conversations_v1_conversation_api.create_service_conversation(
  chat_service_sid,
  friendly_name: friendly_name,
  unique_name: unique_name,
  attributes: attributes,
  messaging_service_sid: messaging_service_sid,
  date_created: date_created,
  date_updated: date_updated,
  state: state,
  timers_inactive: timers_inactive,
  timers_closed: timers_closed
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Service Conversation

Retrieve a list of conversations in your service

```ruby
def list_service_conversation(chat_service_sid,
                              start_date: nil,
                              end_date: nil,
                              state: nil,
                              page_size: nil,
                              page: nil,
                              page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `start_date` | `String` | Query, Optional | Specifies the beginning of the date range for filtering Conversations based on their creation date. Conversations that were created on or after this date will be included in the results. The date must be in ISO8601 format, specifically starting at the beginning of the specified date (YYYY-MM-DDT00:00:00Z), for precise filtering. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `end_date` | `String` | Query, Optional | Defines the end of the date range for filtering conversations by their creation date. Only conversations that were created on or before this date will appear in the results.  The date must be in ISO8601 format, specifically capturing up to the end of the specified date (YYYY-MM-DDT23:59:59Z), to ensure that conversations from the entire end day are included. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `state` | [`ServiceConversationState`](../../doc/models/service-conversation-state.md) | Query, Optional | State for sorting and filtering list of Conversations. Can be `active`, `inactive` or `closed` |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListServiceConversationResponse`](../../doc/models/list-service-conversation-response.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

result = conversations_v1_conversation_api.list_service_conversation(chat_service_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Service Conversation

Update an existing conversation in your service

```ruby
def update_service_conversation(chat_service_sid,
                                sid,
                                x_twilio_webhook_enabled: nil,
                                friendly_name: nil,
                                date_created: nil,
                                date_updated: nil,
                                attributes: nil,
                                messaging_service_sid: nil,
                                state: nil,
                                timers_inactive: nil,
                                timers_closed: nil,
                                unique_name: nil,
                                bindings_email_address: nil,
                                bindings_email_name: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendly_name` | `String` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messaging_service_sid` | `String` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `state` | [`ServiceConversationState`](../../doc/models/service-conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timers_inactive` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timers_closed` | `String` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `unique_name` | `String` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `bindings_email_address` | `String` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindings_email_name` | `String` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversation`](../../doc/models/service-conversation.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

sid = 'Sid8'

friendly_name = 'friendly_name'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "topic": "feedback" }'

messaging_service_sid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaab'

state = ServiceConversationState::INACTIVE

timers_inactive = 'PT1M'

timers_closed = 'PT10M'

unique_name = 'unique_name'

result = conversations_v1_conversation_api.update_service_conversation(
  chat_service_sid,
  sid,
  friendly_name: friendly_name,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  messaging_service_sid: messaging_service_sid,
  state: state,
  timers_inactive: timers_inactive,
  timers_closed: timers_closed,
  unique_name: unique_name
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Service Conversation

Remove a conversation from your service

```ruby
def delete_service_conversation(chat_service_sid,
                                sid,
                                x_twilio_webhook_enabled: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

sid = 'Sid8'

result = conversations_v1_conversation_api.delete_service_conversation(
  chat_service_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Service Conversation

Fetch a conversation from your service

```ruby
def fetch_service_conversation(chat_service_sid,
                               sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversation`](../../doc/models/service-conversation.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

sid = 'Sid8'

result = conversations_v1_conversation_api.fetch_service_conversation(
  chat_service_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

