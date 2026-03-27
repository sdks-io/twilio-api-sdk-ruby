
# Conversation Scoped Webhook

*This model accepts additional fields of type Object.*

## Structure

`ConversationScopedWebhook`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `conversation_sid` | `String` | Optional | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` |
| `target` | `String` | Optional | The target of this webhook: `webhook`, `studio`, `trigger` |
| `url` | `String` | Optional | An absolute API resource URL for this webhook. |
| `configuration` | `Object` | Optional | The configuration of this webhook. Is defined based on target. |
| `date_created` | `DateTime` | Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Optional | The date that this resource was last updated. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "account_sid": "account_sid6",
  "conversation_sid": "conversation_sid6",
  "target": "target8",
  "url": "url4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

