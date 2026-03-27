
# Task Queue Statistics

*This model accepts additional fields of type Object.*

## Structure

`TaskQueueStatistics`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `cumulative` | `Object` | Optional | An object that contains the cumulative statistics for the TaskQueue. |
| `realtime` | `Object` | Optional | An object that contains the real-time statistics for the TaskQueue. |
| `task_queue_sid` | `String` | Optional | The SID of the TaskQueue from which these statistics were calculated.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `workspace_sid` | `String` | Optional | The SID of the Workspace that contains the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `url` | `String` | Optional | The absolute URL of the TaskQueue statistics resource. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "cumulative": {
    "key1": "val1",
    "key2": "val2"
  },
  "realtime": {
    "key1": "val1",
    "key2": "val2"
  },
  "task_queue_sid": "task_queue_sid2",
  "workspace_sid": "workspace_sid6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

