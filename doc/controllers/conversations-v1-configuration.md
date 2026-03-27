# Conversations V1 Configuration

```ruby
conversations_v1_configuration_api = client.conversations_v1_configuration
```

## Class Name

`ConversationsV1ConfigurationApi`

## Methods

* [Fetch Configuration](../../doc/controllers/conversations-v1-configuration.md#fetch-configuration)
* [Update Configuration](../../doc/controllers/conversations-v1-configuration.md#update-configuration)
* [Fetch Service Configuration](../../doc/controllers/conversations-v1-configuration.md#fetch-service-configuration)
* [Update Service Configuration](../../doc/controllers/conversations-v1-configuration.md#update-service-configuration)


# Fetch Configuration

Fetch the global configuration of conversations on your account

```ruby
def fetch_configuration
```

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Configuration`](../../doc/models/configuration.md).

## Example Usage

```ruby
result = conversations_v1_configuration_api.fetch_configuration

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
  "default_chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_inactive_timer": "PT1M",
  "default_closed_timer": "PT10M",
  "url": "https://conversations.twilio.com/v1/Configuration",
  "links": {
    "service": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
    "webhooks": "https://conversations.twilio.com/v1/Configuration/Webhooks"
  }
}
```


# Update Configuration

Update the global configuration of conversations on your account

```ruby
def update_configuration(default_chat_service_sid: nil,
                         default_messaging_service_sid: nil,
                         default_inactive_timer: nil,
                         default_closed_timer: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `default_chat_service_sid` | `String` | Form, Optional | The SID of the default [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to use when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `default_messaging_service_sid` | `String` | Form, Optional | The SID of the default [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) to use when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `default_inactive_timer` | `String` | Form, Optional | Default ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `default_closed_timer` | `String` | Form, Optional | Default ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Configuration`](../../doc/models/configuration.md).

## Example Usage

```ruby
default_chat_service_sid = 'ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

default_messaging_service_sid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

default_inactive_timer = 'PT1M'

default_closed_timer = 'PT10M'

result = conversations_v1_configuration_api.update_configuration(
  default_chat_service_sid: default_chat_service_sid,
  default_messaging_service_sid: default_messaging_service_sid,
  default_inactive_timer: default_inactive_timer,
  default_closed_timer: default_closed_timer
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
  "default_chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_inactive_timer": "PT1M",
  "default_closed_timer": "PT10M",
  "url": "https://conversations.twilio.com/v1/Configuration",
  "links": {
    "service": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
    "webhooks": "https://conversations.twilio.com/v1/Configuration/Webhooks"
  }
}
```


# Fetch Service Configuration

Fetch the configuration of a conversation service

```ruby
def fetch_service_configuration(chat_service_sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the Service configuration resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConfiguration`](../../doc/models/service-configuration.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

result = conversations_v1_configuration_api.fetch_service_configuration(chat_service_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_creator_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_chat_service_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "reachability_enabled": false,
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
  "links": {
    "notifications": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Notifications",
    "webhooks": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
  }
}
```


# Update Service Configuration

Update configuration settings of a conversation service

```ruby
def update_service_configuration(chat_service_sid,
                                 default_conversation_creator_role_sid: nil,
                                 default_conversation_role_sid: nil,
                                 default_chat_service_role_sid: nil,
                                 reachability_enabled: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the Service configuration resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `default_conversation_creator_role_sid` | `String` | Form, Optional | The conversation-level role assigned to a conversation creator when they join a new conversation. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `default_conversation_role_sid` | `String` | Form, Optional | The conversation-level role assigned to users when they are added to a conversation. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `default_chat_service_role_sid` | `String` | Form, Optional | The service-level role assigned to users when they are added to the service. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `reachability_enabled` | `TrueClass \| FalseClass` | Form, Optional | Whether the [Reachability Indicator](https://www.twilio.com/docs/conversations/reachability) is enabled for this Conversations Service. The default is `false`. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceConfiguration`](../../doc/models/service-configuration.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

default_conversation_creator_role_sid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

default_conversation_role_sid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

default_chat_service_role_sid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

reachability_enabled = false

result = conversations_v1_configuration_api.update_service_configuration(
  chat_service_sid,
  default_conversation_creator_role_sid: default_conversation_creator_role_sid,
  default_conversation_role_sid: default_conversation_role_sid,
  default_chat_service_role_sid: default_chat_service_role_sid,
  reachability_enabled: reachability_enabled
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
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_creator_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_chat_service_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "reachability_enabled": false,
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
  "links": {
    "notifications": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Notifications",
    "webhooks": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
  }
}
```

