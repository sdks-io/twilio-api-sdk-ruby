# Taskrouter V1 Task Queue Statistics

```ruby
taskrouter_v1_task_queue_statistics_api = client.taskrouter_v1_task_queue_statistics
```

## Class Name

`TaskrouterV1TaskQueueStatisticsApi`


# Fetch Task Queue Statistics

```ruby
def fetch_task_queue_statistics(workspace_sid,
                                task_queue_sid,
                                end_date: nil,
                                minutes: nil,
                                start_date: nil,
                                task_channel: nil,
                                split_by_wait_time: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the TaskQueue to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `task_queue_sid` | `String` | Template, Required | The SID of the TaskQueue for which to fetch statistics.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `end_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `minutes` | `Integer` | Query, Optional | Only calculate statistics since this many minutes in the past. The default is 15 minutes. |
| `start_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `task_channel` | `String` | Query, Optional | Only calculate real-time and cumulative statistics for the specified TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `split_by_wait_time` | `String` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`TaskQueueStatistics`](../../doc/models/task-queue-statistics.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

task_queue_sid = 'TaskQueueSid8'

end_date = DateTimeHelper.from_rfc3339('01/02/2008 00:00:00')

minutes = 1

start_date = DateTimeHelper.from_rfc3339('01/02/2008 00:00:00')

result = taskrouter_v1_task_queue_statistics_api.fetch_task_queue_statistics(
  workspace_sid,
  task_queue_sid,
  end_date: end_date,
  minutes: minutes,
  start_date: start_date
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

