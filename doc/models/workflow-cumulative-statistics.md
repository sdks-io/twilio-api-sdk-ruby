
# Workflow Cumulative Statistics

*This model accepts additional fields of type Object.*

## Structure

`WorkflowCumulativeStatistics`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Workflow resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `avg_task_acceptance_time` | `Integer` | Optional | The average time in seconds between Task creation and acceptance.<br><br>**Default**: `0` |
| `start_time` | `DateTime` | Optional | The beginning of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `end_time` | `DateTime` | Optional | The end of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `reservations_created` | `Integer` | Optional | The total number of Reservations that were created for Workers.<br><br>**Default**: `0` |
| `reservations_accepted` | `Integer` | Optional | The total number of Reservations accepted by Workers.<br><br>**Default**: `0` |
| `reservations_rejected` | `Integer` | Optional | The total number of Reservations that were rejected.<br><br>**Default**: `0` |
| `reservations_timed_out` | `Integer` | Optional | The total number of Reservations that were timed out.<br><br>**Default**: `0` |
| `reservations_canceled` | `Integer` | Optional | The total number of Reservations that were canceled.<br><br>**Default**: `0` |
| `reservations_rescinded` | `Integer` | Optional | The total number of Reservations that were rescinded.<br><br>**Default**: `0` |
| `split_by_wait_time` | `Object` | Optional | A list of objects that describe the number of Tasks canceled and reservations accepted above and below the thresholds specified in seconds. |
| `wait_duration_until_accepted` | `Object` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks that were accepted. |
| `wait_duration_until_canceled` | `Object` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks that were canceled. |
| `tasks_canceled` | `Integer` | Optional | The total number of Tasks that were canceled.<br><br>**Default**: `0` |
| `tasks_completed` | `Integer` | Optional | The total number of Tasks that were completed.<br><br>**Default**: `0` |
| `tasks_entered` | `Integer` | Optional | The total number of Tasks that entered the Workflow.<br><br>**Default**: `0` |
| `tasks_deleted` | `Integer` | Optional | The total number of Tasks that were deleted.<br><br>**Default**: `0` |
| `tasks_moved` | `Integer` | Optional | The total number of Tasks that were moved from one queue to another.<br><br>**Default**: `0` |
| `tasks_timed_out_in_workflow` | `Integer` | Optional | The total number of Tasks that were timed out of their Workflows (and deleted).<br><br>**Default**: `0` |
| `workflow_sid` | `String` | Optional | Returns the list of Tasks that are being controlled by the Workflow with the specified Sid value.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `workspace_sid` | `String` | Optional | The SID of the Workspace that contains the Workflow.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `url` | `String` | Optional | The absolute URL of the Workflow statistics resource. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "avg_task_acceptance_time": 0,
  "reservations_created": 0,
  "reservations_accepted": 0,
  "reservations_rejected": 0,
  "reservations_timed_out": 0,
  "reservations_canceled": 0,
  "reservations_rescinded": 0,
  "tasks_canceled": 0,
  "tasks_completed": 0,
  "tasks_entered": 0,
  "tasks_deleted": 0,
  "tasks_moved": 0,
  "tasks_timed_out_in_workflow": 0,
  "account_sid": "account_sid0",
  "start_time": "2016-03-13T12:52:32.123Z",
  "end_time": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

