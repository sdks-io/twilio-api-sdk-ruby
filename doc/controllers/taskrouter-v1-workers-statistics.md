# Taskrouter V1 Workers Statistics

```ruby
taskrouter_v1_workers_statistics_api = client.taskrouter_v1_workers_statistics
```

## Class Name

`TaskrouterV1WorkersStatisticsApi`


# Fetch Worker Statistics

```ruby
def fetch_worker_statistics(workspace_sid,
                            minutes: nil,
                            start_date: nil,
                            end_date: nil,
                            task_queue_sid: nil,
                            task_queue_name: nil,
                            friendly_name: nil,
                            task_channel: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Worker to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `minutes` | `Integer` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `start_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `end_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `task_queue_sid` | `String` | Query, Optional | The SID of the TaskQueue for which to fetch Worker statistics.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `task_queue_name` | `String` | Query, Optional | The `friendly_name` of the TaskQueue for which to fetch Worker statistics. |
| `friendly_name` | `String` | Query, Optional | Only include Workers with `friendly_name` values that match this parameter. |
| `task_channel` | `String` | Query, Optional | Only calculate statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`WorkerStatistics`](../../doc/models/worker-statistics.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

minutes = 1

start_date = DateTimeHelper.from_rfc3339('01/02/2008 00:00:00')

end_date = DateTimeHelper.from_rfc3339('01/02/2008 00:00:00')

result = taskrouter_v1_workers_statistics_api.fetch_worker_statistics(
  workspace_sid,
  minutes: minutes,
  start_date: start_date,
  end_date: end_date
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

