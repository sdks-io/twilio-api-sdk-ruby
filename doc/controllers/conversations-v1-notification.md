# Conversations V1 Notification

```ruby
conversations_v1_notification_api = client.conversations_v1_notification
```

## Class Name

`ConversationsV1NotificationApi`

## Methods

* [Update Service Notification](../../doc/controllers/conversations-v1-notification.md#update-service-notification)
* [Fetch Service Notification](../../doc/controllers/conversations-v1-notification.md#fetch-service-notification)


# Update Service Notification

Update push notification service settings

```ruby
def update_service_notification(chat_service_sid,
                                log_enabled: nil,
                                new_message_enabled: nil,
                                new_message_template: nil,
                                new_message_sound: nil,
                                new_message_badge_count_enabled: nil,
                                added_to_conversation_enabled: nil,
                                added_to_conversation_template: nil,
                                added_to_conversation_sound: nil,
                                removed_from_conversation_enabled: nil,
                                removed_from_conversation_template: nil,
                                removed_from_conversation_sound: nil,
                                new_message_with_media_enabled: nil,
                                new_message_with_media_template: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `log_enabled` | `TrueClass \| FalseClass` | Form, Optional | Weather the notification logging is enabled. |
| `new_message_enabled` | `TrueClass \| FalseClass` | Form, Optional | Whether to send a notification when a new message is added to a conversation. The default is `false`. |
| `new_message_template` | `String` | Form, Optional | The template to use to create the notification text displayed when a new message is added to a conversation and `new_message.enabled` is `true`. |
| `new_message_sound` | `String` | Form, Optional | The name of the sound to play when a new message is added to a conversation and `new_message.enabled` is `true`. |
| `new_message_badge_count_enabled` | `TrueClass \| FalseClass` | Form, Optional | Whether the new message badge is enabled. The default is `false`. |
| `added_to_conversation_enabled` | `TrueClass \| FalseClass` | Form, Optional | Whether to send a notification when a participant is added to a conversation. The default is `false`. |
| `added_to_conversation_template` | `String` | Form, Optional | The template to use to create the notification text displayed when a participant is added to a conversation and `added_to_conversation.enabled` is `true`. |
| `added_to_conversation_sound` | `String` | Form, Optional | The name of the sound to play when a participant is added to a conversation and `added_to_conversation.enabled` is `true`. |
| `removed_from_conversation_enabled` | `TrueClass \| FalseClass` | Form, Optional | Whether to send a notification to a user when they are removed from a conversation. The default is `false`. |
| `removed_from_conversation_template` | `String` | Form, Optional | The template to use to create the notification text displayed to a user when they are removed from a conversation and `removed_from_conversation.enabled` is `true`. |
| `removed_from_conversation_sound` | `String` | Form, Optional | The name of the sound to play to a user when they are removed from a conversation and `removed_from_conversation.enabled` is `true`. |
| `new_message_with_media_enabled` | `TrueClass \| FalseClass` | Form, Optional | Whether to send a notification when a new message with media/file attachments is added to a conversation. The default is `false`. |
| `new_message_with_media_template` | `String` | Form, Optional | The template to use to create the notification text displayed when a new message with media/file attachments is added to a conversation and `new_message.attachments.enabled` is `true`. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceNotification`](../../doc/models/service-notification.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

log_enabled = true

new_message_enabled = false

new_message_template = 'You have a new message in ${CONVERSATION} from ${PARTICIPANT}: ${MESSAGE}'

new_message_sound = 'ring'

new_message_badge_count_enabled = true

added_to_conversation_enabled = false

added_to_conversation_template = 'You have been added to a Conversation: ${CONVERSATION}'

added_to_conversation_sound = 'ring'

removed_from_conversation_enabled = false

removed_from_conversation_template = 'You have been removed from a Conversation: ${CONVERSATION}'

removed_from_conversation_sound = 'ring'

new_message_with_media_enabled = false

new_message_with_media_template = 'You have a new message in ${CONVERSATION} with ${MEDIA_COUNT} media files: ${MEDIA}'

result = conversations_v1_notification_api.update_service_notification(
  chat_service_sid,
  log_enabled: log_enabled,
  new_message_enabled: new_message_enabled,
  new_message_template: new_message_template,
  new_message_sound: new_message_sound,
  new_message_badge_count_enabled: new_message_badge_count_enabled,
  added_to_conversation_enabled: added_to_conversation_enabled,
  added_to_conversation_template: added_to_conversation_template,
  added_to_conversation_sound: added_to_conversation_sound,
  removed_from_conversation_enabled: removed_from_conversation_enabled,
  removed_from_conversation_template: removed_from_conversation_template,
  removed_from_conversation_sound: removed_from_conversation_sound,
  new_message_with_media_enabled: new_message_with_media_enabled,
  new_message_with_media_template: new_message_with_media_template
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Service Notification

Fetch push notification service settings

```ruby
def fetch_service_notification(chat_service_sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceNotification`](../../doc/models/service-notification.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

result = conversations_v1_notification_api.fetch_service_notification(chat_service_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

