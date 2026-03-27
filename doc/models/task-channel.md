
# Task Channel

*This model accepts additional fields of type Object.*

## Structure

`TaskChannel`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Task Channel resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `date_created` | `DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `date_updated` | `DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `friendly_name` | `String` | Optional | The string that you assigned to describe the resource. |
| `sid` | `String` | Optional | The unique string that we created to identify the Task Channel resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^TC[0-9a-fA-F]{32}$` |
| `unique_name` | `String` | Optional | An application-defined string that uniquely identifies the Task Channel, such as `voice` or `sms`. |
| `workspace_sid` | `String` | Optional | The SID of the Workspace that contains the Task Channel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `channel_optimized_routing` | `TrueClass \| FalseClass` | Optional | Whether the Task Channel will prioritize Workers that have been idle. When `true`, Workers that have been idle the longest are prioritized. |
| `url` | `String` | Optional | The absolute URL of the Task Channel resource. |
| `links` | `Object` | Optional | The URLs of related resources. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "friendly_name": "friendly_name4",
  "sid": "sid0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

