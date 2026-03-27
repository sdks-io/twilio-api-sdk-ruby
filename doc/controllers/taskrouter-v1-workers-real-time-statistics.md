# Taskrouter V1 Workers Real Time Statistics

```ruby
taskrouter_v1_workers_real_time_statistics_api = client.taskrouter_v1_workers_real_time_statistics
```

## Class Name

`TaskrouterV1WorkersRealTimeStatisticsApi`


# Fetch Workers Real Time Statistics

```ruby
def fetch_workers_real_time_statistics(workspace_sid,
                                       task_channel: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `task_channel` | `String` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`WorkersRealTimeStatistics`](../../doc/models/workers-real-time-statistics.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

task_channel = 'voice'

result = taskrouter_v1_workers_real_time_statistics_api.fetch_workers_real_time_statistics(
  workspace_sid,
  task_channel: task_channel
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
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/RealTimeStatistics",
  "total_workers": 15,
  "activity_statistics": [
    {
      "friendly_name": "Idle",
      "workers": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "friendly_name": "Busy",
      "workers": 9,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "friendly_name": "Offline",
      "workers": 6,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "friendly_name": "Reserved",
      "workers": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```

