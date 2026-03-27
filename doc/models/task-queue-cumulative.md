
# Task Queue Cumulative

*This model accepts additional fields of type Object.*

## Structure

`TaskQueueCumulative`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `avg_task_acceptance_time` | `Integer` | Optional | The average time in seconds between Task creation and acceptance.<br><br>**Default**: `0` |
| `start_time` | `DateTime` | Optional | The beginning of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `end_time` | `DateTime` | Optional | The end of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `reservations_created` | `Integer` | Optional | The total number of Reservations created for Tasks in the TaskQueue.<br><br>**Default**: `0` |
| `reservations_accepted` | `Integer` | Optional | The total number of Reservations accepted for Tasks in the TaskQueue.<br><br>**Default**: `0` |
| `reservations_rejected` | `Integer` | Optional | The total number of Reservations rejected for Tasks in the TaskQueue.<br><br>**Default**: `0` |
| `reservations_timed_out` | `Integer` | Optional | The total number of Reservations that timed out for Tasks in the TaskQueue.<br><br>**Default**: `0` |
| `reservations_canceled` | `Integer` | Optional | The total number of Reservations canceled for Tasks in the TaskQueue.<br><br>**Default**: `0` |
| `reservations_rescinded` | `Integer` | Optional | The total number of Reservations rescinded.<br><br>**Default**: `0` |
| `split_by_wait_time` | `Object` | Optional | A list of objects that describe the number of Tasks canceled and reservations accepted above and below the thresholds specified in seconds. |
| `task_queue_sid` | `String` | Optional | The SID of the TaskQueue from which these statistics were calculated.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `wait_duration_until_accepted` | `Object` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks accepted while in the TaskQueue. Calculation is based on the time when the Tasks were created. For transfers, the wait duration is counted from the moment ***the Task was created***, and not from when the transfer was initiated. |
| `wait_duration_until_canceled` | `Object` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks canceled while in the TaskQueue. |
| `wait_duration_in_queue_until_accepted` | `Object` | Optional | The relative wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks accepted while in the TaskQueue. Calculation is based on the time when the Tasks entered the TaskQueue. |
| `tasks_canceled` | `Integer` | Optional | The total number of Tasks canceled in the TaskQueue.<br><br>**Default**: `0` |
| `tasks_completed` | `Integer` | Optional | The total number of Tasks completed in the TaskQueue.<br><br>**Default**: `0` |
| `tasks_deleted` | `Integer` | Optional | The total number of Tasks deleted in the TaskQueue.<br><br>**Default**: `0` |
| `tasks_entered` | `Integer` | Optional | The total number of Tasks entered into the TaskQueue.<br><br>**Default**: `0` |
| `tasks_moved` | `Integer` | Optional | The total number of Tasks that were moved from one queue to another.<br><br>**Default**: `0` |
| `workspace_sid` | `String` | Optional | The SID of the Workspace that contains the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `url` | `String` | Optional | The absolute URL of the TaskQueue statistics resource. |
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
  "tasks_deleted": 0,
  "tasks_entered": 0,
  "tasks_moved": 0,
  "account_sid": "account_sid2",
  "start_time": "2016-03-13T12:52:32.123Z",
  "end_time": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

