# Conversations V1 Participant Conversation

```ruby
conversations_v1_participant_conversation_api = client.conversations_v1_participant_conversation
```

## Class Name

`ConversationsV1ParticipantConversationApi`

## Methods

* [List Participant Conversation](../../doc/controllers/conversations-v1-participant-conversation.md#list-participant-conversation)
* [List Service Participant Conversation](../../doc/controllers/conversations-v1-participant-conversation.md#list-service-participant-conversation)


# List Participant Conversation

Retrieve a list of all Conversations that this Participant belongs to by identity or by address. Only one parameter should be specified.

```ruby
def list_participant_conversation(identity: nil,
                                  address: nil,
                                  page_size: nil,
                                  page: nil,
                                  page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `identity` | `String` | Query, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `address` | `String` | Query, Optional | A unique string identifier for the conversation participant who's not a Conversation User. This parameter could be found in messaging_binding.address field of Participant resource. It should be url-encoded. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListParticipantConversationResponse`](../../doc/models/list-participant-conversation-response.md).

## Example Usage

```ruby
identity = 'identity'

address = '+375255555555'

result = conversations_v1_participant_conversation_api.list_participant_conversation(
  identity: identity,
  address: address
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
    "first_page_url": "https://conversations.twilio.com/v1/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```


# List Service Participant Conversation

Retrieve a list of all Conversations that this Participant belongs to by identity or by address. Only one parameter should be specified.

```ruby
def list_service_participant_conversation(chat_service_sid,
                                          identity: nil,
                                          address: nil,
                                          page_size: nil,
                                          page: nil,
                                          page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant Conversations resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `identity` | `String` | Query, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `address` | `String` | Query, Optional | A unique string identifier for the conversation participant who's not a Conversation User. This parameter could be found in messaging_binding.address field of Participant resource. It should be url-encoded. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListServiceParticipantConversationResponse`](../../doc/models/list-service-participant-conversation-response.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

identity = 'identity'

address = '+375255555555'

result = conversations_v1_participant_conversation_api.list_service_participant_conversation(
  chat_service_sid,
  identity: identity,
  address: address
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
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```

