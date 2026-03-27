# Conversations V1 User Conversation

```ruby
conversations_v1_user_conversation_api = client.conversations_v1_user_conversation
```

## Class Name

`ConversationsV1UserConversationApi`

## Methods

* [Update Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#update-service-user-conversation)
* [Delete Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#delete-service-user-conversation)
* [Fetch Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#fetch-service-user-conversation)
* [List Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#list-service-user-conversation)
* [Update User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#update-user-conversation)
* [Delete User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#delete-user-conversation)
* [Fetch User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#fetch-user-conversation)
* [List User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#list-user-conversation)


# Update Service User Conversation

Update a specific User Conversation.

```ruby
def update_service_user_conversation(chat_service_sid,
                                     user_sid,
                                     conversation_sid,
                                     notification_level: nil,
                                     last_read_timestamp: nil,
                                     last_read_message_index: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversation_sid` | `String` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |
| `notification_level` | [`ServiceUserConversationNotificationLevel`](../../doc/models/service-user-conversation-notification-level.md) | Form, Optional | The Notification Level of this User Conversation. One of `default` or `muted`. |
| `last_read_timestamp` | `DateTime` | Form, Optional | The date of the last message read in conversation by the user, given in ISO 8601 format. |
| `last_read_message_index` | `Integer` | Form, Optional | The index of the last Message in the Conversation that the Participant has read. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceUserConversation`](../../doc/models/service-user-conversation.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

user_sid = 'UserSid6'

conversation_sid = 'ConversationSid0'

notification_level = ServiceUserConversationNotificationLevel::DEFAULT

last_read_timestamp = DateTimeHelper.from_rfc3339('07/30/2015 20:00:00')

last_read_message_index = 100

result = conversations_v1_user_conversation_api.update_service_user_conversation(
  chat_service_sid,
  user_sid,
  conversation_sid,
  notification_level: notification_level,
  last_read_timestamp: last_read_timestamp,
  last_read_message_index: last_read_message_index
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete Service User Conversation

Delete a specific User Conversation.

```ruby
def delete_service_user_conversation(chat_service_sid,
                                     user_sid,
                                     conversation_sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversation_sid` | `String` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

user_sid = 'UserSid6'

conversation_sid = 'ConversationSid0'

result = conversations_v1_user_conversation_api.delete_service_user_conversation(
  chat_service_sid,
  user_sid,
  conversation_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Service User Conversation

Fetch a specific User Conversation.

```ruby
def fetch_service_user_conversation(chat_service_sid,
                                    user_sid,
                                    conversation_sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversation_sid` | `String` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceUserConversation`](../../doc/models/service-user-conversation.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

user_sid = 'UserSid6'

conversation_sid = 'ConversationSid0'

result = conversations_v1_user_conversation_api.fetch_service_user_conversation(
  chat_service_sid,
  user_sid,
  conversation_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Service User Conversation

Retrieve a list of all User Conversations for the User.

```ruby
def list_service_user_conversation(chat_service_sid,
                                   user_sid,
                                   page_size: nil,
                                   page: nil,
                                   page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListServiceUserConversationResponse`](../../doc/models/list-service-user-conversation-response.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

user_sid = 'UserSid6'

result = conversations_v1_user_conversation_api.list_service_user_conversation(
  chat_service_sid,
  user_sid
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
  "conversations": [],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```


# Update User Conversation

Update a specific User Conversation.

```ruby
def update_user_conversation(user_sid,
                             conversation_sid,
                             notification_level: nil,
                             last_read_timestamp: nil,
                             last_read_message_index: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversation_sid` | `String` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |
| `notification_level` | [`UserConversationNotificationLevel`](../../doc/models/user-conversation-notification-level.md) | Form, Optional | The Notification Level of this User Conversation. One of `default` or `muted`. |
| `last_read_timestamp` | `DateTime` | Form, Optional | The date of the last message read in conversation by the user, given in ISO 8601 format. |
| `last_read_message_index` | `Integer` | Form, Optional | The index of the last Message in the Conversation that the Participant has read. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`UserConversation`](../../doc/models/user-conversation.md).

## Example Usage

```ruby
user_sid = 'UserSid6'

conversation_sid = 'ConversationSid0'

notification_level = UserConversationNotificationLevel::DEFAULT

last_read_timestamp = DateTimeHelper.from_rfc3339('07/30/2015 20:00:00')

last_read_message_index = 100

result = conversations_v1_user_conversation_api.update_user_conversation(
  user_sid,
  conversation_sid,
  notification_level: notification_level,
  last_read_timestamp: last_read_timestamp,
  last_read_message_index: last_read_message_index
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Delete User Conversation

Delete a specific User Conversation.

```ruby
def delete_user_conversation(user_sid,
                             conversation_sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversation_sid` | `String` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
user_sid = 'UserSid6'

conversation_sid = 'ConversationSid0'

result = conversations_v1_user_conversation_api.delete_user_conversation(
  user_sid,
  conversation_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch User Conversation

Fetch a specific User Conversation.

```ruby
def fetch_user_conversation(user_sid,
                            conversation_sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversation_sid` | `String` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`UserConversation`](../../doc/models/user-conversation.md).

## Example Usage

```ruby
user_sid = 'UserSid6'

conversation_sid = 'ConversationSid0'

result = conversations_v1_user_conversation_api.fetch_user_conversation(
  user_sid,
  conversation_sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List User Conversation

Retrieve a list of all User Conversations for the User.

```ruby
def list_user_conversation(user_sid,
                           page_size: nil,
                           page: nil,
                           page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `user_sid` | `String` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListUserConversationResponse`](../../doc/models/list-user-conversation-response.md).

## Example Usage

```ruby
user_sid = 'UserSid6'

result = conversations_v1_user_conversation_api.list_user_conversation(user_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "conversations": [],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```

