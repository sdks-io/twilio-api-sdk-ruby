# Taskrouter V1 Workers Cumulative Statistics

```ruby
taskrouter_v1_workers_cumulative_statistics_api = client.taskrouter_v1_workers_cumulative_statistics
```

## Class Name

`TaskrouterV1WorkersCumulativeStatisticsApi`


# Fetch Workers Cumulative Statistics

```ruby
def fetch_workers_cumulative_statistics(workspace_sid,
                                        end_date: nil,
                                        minutes: nil,
                                        start_date: nil,
                                        task_channel: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `end_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `minutes` | `Integer` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `start_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `task_channel` | `String` | Query, Optional | Only calculate cumulative statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`WorkersCumulativeStatistics`](../../doc/models/workers-cumulative-statistics.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

end_date = DateTimeHelper.from_rfc3339('07/30/2015 20:00:00')

start_date = DateTimeHelper.from_rfc3339('07/30/2015 20:00:00')

result = taskrouter_v1_workers_cumulative_statistics_api.fetch_workers_cumulative_statistics(
  workspace_sid,
  end_date: end_date,
  start_date: start_date
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
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/CumulativeStatistics",
  "reservations_created": 100,
  "reservations_accepted": 100,
  "reservations_rejected": 100,
  "reservations_timed_out": 100,
  "reservations_canceled": 100,
  "reservations_rescinded": 100,
  "activity_durations": [
    {
      "max": 0,
      "min": 900,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Offline",
      "avg": 1080,
      "total": 5400
    },
    {
      "max": 0,
      "min": 900,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Busy",
      "avg": 1012,
      "total": 8100
    },
    {
      "max": 0,
      "min": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Idle",
      "avg": 0,
      "total": 0
    },
    {
      "max": 0,
      "min": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Reserved",
      "avg": 0,
      "total": 0
    }
  ],
  "start_time": "2015-07-30T20:00:00Z",
  "end_time": "2015-07-30T20:00:00Z"
}
```

