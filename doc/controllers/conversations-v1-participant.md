# Conversations V1 Participant

```ruby
conversations_v1_participant_api = client.conversations_v1_participant
```

## Class Name

`ConversationsV1ParticipantApi`

## Methods

* [Create Conversation Participant](../../doc/controllers/conversations-v1-participant.md#create-conversation-participant)
* [List Conversation Participant](../../doc/controllers/conversations-v1-participant.md#list-conversation-participant)
* [Update Conversation Participant](../../doc/controllers/conversations-v1-participant.md#update-conversation-participant)
* [Delete Conversation Participant](../../doc/controllers/conversations-v1-participant.md#delete-conversation-participant)
* [Fetch Conversation Participant](../../doc/controllers/conversations-v1-participant.md#fetch-conversation-participant)
* [Create Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#create-service-conversation-participant)
* [List Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#list-service-conversation-participant)
* [Update Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#update-service-conversation-participant)
* [Delete Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#delete-service-conversation-participant)
* [Fetch Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#fetch-service-conversation-participant)


# Create Conversation Participant

Add a new participant to the conversation

```ruby
def create_conversation_participant(conversation_sid,
                                    x_twilio_webhook_enabled: nil,
                                    identity: nil,
                                    messaging_binding_address: nil,
                                    messaging_binding_proxy_address: nil,
                                    date_created: nil,
                                    date_updated: nil,
                                    attributes: nil,
                                    messaging_binding_projected_address: nil,
                                    role_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `identity` | `String` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `messaging_binding_address` | `String` | Form, Optional | The address of the participant's device, e.g. a phone or WhatsApp number. Together with the Proxy address, this determines a participant uniquely. This field (with proxy_address) is only null when the participant is interacting from an SDK endpoint (see the 'identity' field). |
| `messaging_binding_proxy_address` | `String` | Form, Optional | The address of the Twilio phone number (or WhatsApp number) that the participant is in contact with. This field, together with participant address, is only null when the participant is interacting from an SDK endpoint (see the 'identity' field). |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messaging_binding_projected_address` | `String` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. Communication mask for the Conversation participant with Identity. |
| `role_sid` | `String` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationParticipant`](../../doc/models/conversation-participant.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

identity = 'IDENTITY'

messaging_binding_address = '+15558675310'

messaging_binding_proxy_address = '+15017122661'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "role": "driver" }'

messaging_binding_projected_address = '+15017122661'

role_sid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = conversations_v1_participant_api.create_conversation_participant(
  conversation_sid,
  identity: identity,
  messaging_binding_address: messaging_binding_address,
  messaging_binding_proxy_address: messaging_binding_proxy_address,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  messaging_binding_projected_address: messaging_binding_projected_address,
  role_sid: role_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Conversation Participant

Retrieve a list of all participants of the conversation

```ruby
def list_conversation_participant(conversation_sid,
                                  page_size: nil,
                                  page: nil,
                                  page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for participants. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListConversationParticipantResponse`](../../doc/models/list-conversation-participant-response.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

result = conversations_v1_participant_api.list_conversation_participant(conversation_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Conversation Participant

Update an existing participant in the conversation

```ruby
def update_conversation_participant(conversation_sid,
                                    sid,
                                    x_twilio_webhook_enabled: nil,
                                    date_created: nil,
                                    date_updated: nil,
                                    attributes: nil,
                                    role_sid: nil,
                                    messaging_binding_proxy_address: nil,
                                    messaging_binding_projected_address: nil,
                                    identity: nil,
                                    last_read_message_index: nil,
                                    last_read_timestamp: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `date_created` | `DateTime` | Form, Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `role_sid` | `String` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `messaging_binding_proxy_address` | `String` | Form, Optional | The address of the Twilio phone number that the participant is in contact with. 'null' value will remove it. |
| `messaging_binding_projected_address` | `String` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. 'null' value will remove it. |
| `identity` | `String` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `last_read_message_index` | `Integer` | Form, Optional | Index of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |
| `last_read_timestamp` | `String` | Form, Optional | Timestamp of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationParticipant`](../../doc/models/conversation-participant.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "role": "driver" }'

role_sid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

messaging_binding_projected_address = '+15017122661'

result = conversations_v1_participant_api.update_conversation_participant(
  conversation_sid,
  sid,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  role_sid: role_sid,
  messaging_binding_projected_address: messaging_binding_projected_address
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Conversation Participant

Remove a participant from the conversation

```ruby
def delete_conversation_participant(conversation_sid,
                                    sid,
                                    x_twilio_webhook_enabled: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_participant_api.delete_conversation_participant(
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Conversation Participant

Fetch a participant of the conversation

```ruby
def fetch_conversation_participant(conversation_sid,
                                   sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Alternatively, you can pass a Participant's `identity` rather than the SID. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ConversationParticipant`](../../doc/models/conversation-participant.md).

## Example Usage

```ruby
conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_participant_api.fetch_conversation_participant(
  conversation_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Create Service Conversation Participant

Add a new participant to the conversation in a specific service

```ruby
def create_service_conversation_participant(chat_service_sid,
                                            conversation_sid,
                                            x_twilio_webhook_enabled: nil,
                                            identity: nil,
                                            messaging_binding_address: nil,
                                            messaging_binding_proxy_address: nil,
                                            date_created: nil,
                                            date_updated: nil,
                                            attributes: nil,
                                            messaging_binding_projected_address: nil,
                                            role_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `identity` | `String` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the [Conversation SDK](https://www.twilio.com/docs/conversations/sdk-overview) to communicate. Limited to 256 characters. |
| `messaging_binding_address` | `String` | Form, Optional | The address of the participant's device, e.g. a phone or WhatsApp number. Together with the Proxy address, this determines a participant uniquely. This field (with `proxy_address`) is only null when the participant is interacting from an SDK endpoint (see the `identity` field). |
| `messaging_binding_proxy_address` | `String` | Form, Optional | The address of the Twilio phone number (or WhatsApp number) that the participant is in contact with. This field, together with participant address, is only null when the participant is interacting from an SDK endpoint (see the `identity` field). |
| `date_created` | `DateTime` | Form, Optional | The date on which this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date on which this resource was last updated. |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set `{}` will be returned. |
| `messaging_binding_projected_address` | `String` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. |
| `role_sid` | `String` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationParticipant`](../../doc/models/service-conversation-participant.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

identity = 'IDENTITY'

messaging_binding_address = '+15558675310'

messaging_binding_proxy_address = '+15017122661'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "role": "driver" }'

messaging_binding_projected_address = '+15017122661'

role_sid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = conversations_v1_participant_api.create_service_conversation_participant(
  chat_service_sid,
  conversation_sid,
  identity: identity,
  messaging_binding_address: messaging_binding_address,
  messaging_binding_proxy_address: messaging_binding_proxy_address,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  messaging_binding_projected_address: messaging_binding_projected_address,
  role_sid: role_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Service Conversation Participant

Retrieve a list of all participants of the conversation

```ruby
def list_service_conversation_participant(chat_service_sid,
                                          conversation_sid,
                                          page_size: nil,
                                          page: nil,
                                          page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for participants. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListServiceConversationParticipantResponse`](../../doc/models/list-service-conversation-participant-response.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

result = conversations_v1_participant_api.list_service_conversation_participant(
  chat_service_sid,
  conversation_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Update Service Conversation Participant

Update an existing participant in the conversation

```ruby
def update_service_conversation_participant(chat_service_sid,
                                            conversation_sid,
                                            sid,
                                            x_twilio_webhook_enabled: nil,
                                            date_created: nil,
                                            date_updated: nil,
                                            identity: nil,
                                            attributes: nil,
                                            role_sid: nil,
                                            messaging_binding_proxy_address: nil,
                                            messaging_binding_projected_address: nil,
                                            last_read_message_index: nil,
                                            last_read_timestamp: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `date_created` | `DateTime` | Form, Optional | The date on which this resource was created. |
| `date_updated` | `DateTime` | Form, Optional | The date on which this resource was last updated. |
| `identity` | `String` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the [Conversation SDK](https://www.twilio.com/docs/conversations/sdk-overview) to communicate. Limited to 256 characters. |
| `attributes` | `String` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set `{}` will be returned. |
| `role_sid` | `String` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `messaging_binding_proxy_address` | `String` | Form, Optional | The address of the Twilio phone number that the participant is in contact with. 'null' value will remove it. |
| `messaging_binding_projected_address` | `String` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. 'null' value will remove it. |
| `last_read_message_index` | `Integer` | Form, Optional | Index of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |
| `last_read_timestamp` | `String` | Form, Optional | Timestamp of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationParticipant`](../../doc/models/service-conversation-participant.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

date_created = DateTimeHelper.from_rfc3339('12/16/2015 22:18:37')

date_updated = DateTimeHelper.from_rfc3339('12/16/2015 22:18:38')

attributes = '{ "role": "driver" }'

role_sid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

messaging_binding_projected_address = '+15017122661'

result = conversations_v1_participant_api.update_service_conversation_participant(
  chat_service_sid,
  conversation_sid,
  sid,
  date_created: date_created,
  date_updated: date_updated,
  attributes: attributes,
  role_sid: role_sid,
  messaging_binding_projected_address: messaging_binding_projected_address
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Service Conversation Participant

Remove a participant from the conversation

```ruby
def delete_service_conversation_participant(chat_service_sid,
                                            conversation_sid,
                                            sid,
                                            x_twilio_webhook_enabled: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. |
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

result = conversations_v1_participant_api.delete_service_conversation_participant(
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


# Fetch Service Conversation Participant

Fetch a participant of the conversation

```ruby
def fetch_service_conversation_participant(chat_service_sid,
                                           conversation_sid,
                                           sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource. Alternatively, you can pass a Participant's `identity` rather than the SID. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConversationParticipant`](../../doc/models/service-conversation-participant.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

conversation_sid = 'ConversationSid0'

sid = 'Sid8'

result = conversations_v1_participant_api.fetch_service_conversation_participant(
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

