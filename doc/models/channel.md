
# Channel

*This model accepts additional fields of type Object.*

## Structure

`Channel`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | The unique string that we created to identify the Channel resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Channel resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `service_sid` | `String` | Optional | The SID of the [Service](https://www.twilio.com/docs/chat/rest/service-resource) the Channel resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Optional | The string that you assigned to describe the resource. |
| `unique_name` | `String` | Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `attributes` | `String` | Optional | The JSON string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `type` | [`ChannelChannelType`](../../doc/models/channel-channel-type.md) | Optional | The visibility of the channel. Can be: `public` or `private`. |
| `date_created` | `DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `date_updated` | `DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `created_by` | `String` | Optional | The `identity` of the User that created the channel. If the Channel was created by using the API, the value is `system`. |
| `members_count` | `Integer` | Optional | The number of Members in the Channel.<br><br>**Default**: `0` |
| `messages_count` | `Integer` | Optional | The number of Messages that have been passed in the Channel.<br><br>**Default**: `0` |
| `messaging_service_sid` | `String` | Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this channel belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `url` | `String` | Optional | The absolute URL of the Channel resource. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "members_count": 0,
  "messages_count": 0,
  "sid": "sid0",
  "account_sid": "account_sid4",
  "service_sid": "service_sid4",
  "friendly_name": "friendly_name4",
  "unique_name": "unique_name8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

