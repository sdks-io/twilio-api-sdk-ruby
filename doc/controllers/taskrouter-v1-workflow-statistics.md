# Taskrouter V1 Workflow Statistics

```ruby
taskrouter_v1_workflow_statistics_api = client.taskrouter_v1_workflow_statistics
```

## Class Name

`TaskrouterV1WorkflowStatisticsApi`


# Fetch Workflow Statistics

```ruby
def fetch_workflow_statistics(workspace_sid,
                              workflow_sid,
                              minutes: nil,
                              start_date: nil,
                              end_date: nil,
                              task_channel: nil,
                              split_by_wait_time: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Workflow to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `workflow_sid` | `String` | Template, Required | Returns the list of Tasks that are being controlled by the Workflow with the specified SID value.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `minutes` | `Integer` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `start_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `end_date` | `DateTime` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `task_channel` | `String` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `split_by_wait_time` | `String` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. For example, `5,30` would show splits of Tasks that were canceled or accepted before and after 5 seconds and before and after 30 seconds. This can be used to show short abandoned Tasks or Tasks that failed to meet an SLA. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`WorkflowStatistics`](../../doc/models/workflow-statistics.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

workflow_sid = 'WorkflowSid4'

minutes = 1

start_date = DateTimeHelper.from_rfc3339('01/02/2008 00:00:00')

end_date = DateTimeHelper.from_rfc3339('01/02/2008 00:00:00')

result = taskrouter_v1_workflow_statistics_api.fetch_workflow_statistics(
  workspace_sid,
  workflow_sid,
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

