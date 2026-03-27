# Chat V3 Channel

```ruby
chat_v3_channel_api = client.chat_v3_channel
```

## Class Name

`ChatV3ChannelApi`


# Update Channel

Update a specific Channel.

```ruby
def update_channel(service_sid,
                   sid,
                   x_twilio_webhook_enabled: nil,
                   type: nil,
                   messaging_service_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `service_sid` | `String` | Template, Required | The unique SID identifier of the Service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this Channel. |
| `x_twilio_webhook_enabled` | [`ChannelWebhookEnabledType`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `type` | [`ChannelChannelType`](../../doc/models/channel-channel-type.md) | Form, Optional | The visibility of the channel. Can be: `public` or `private`. |
| `messaging_service_sid` | `String` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this channel belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT1`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Channel`](../../doc/models/channel.md).

## Example Usage

```ruby
service_sid = 'ServiceSid8'

sid = 'Sid8'

type = ChannelChannelType::PRIVATE

messaging_service_sid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = chat_v3_channel_api.update_channel(
  service_sid,
  sid,
  type: type,
  messaging_service_sid: messaging_service_sid
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
  "sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "friendly_name",
  "unique_name": "unique_name",
  "attributes": "{ \"foo\": \"bar\" }",
  "type": "public",
  "date_created": "2015-12-16T22:18:37Z",
  "date_updated": "2015-12-16T22:18:38Z",
  "created_by": "username",
  "members_count": 0,
  "messages_count": 0,
  "url": "https://chat.twilio.com/v3/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

