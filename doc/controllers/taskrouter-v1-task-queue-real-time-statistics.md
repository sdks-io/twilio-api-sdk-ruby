# Taskrouter V1 Task Queue Real Time Statistics

```ruby
taskrouter_v1_task_queue_real_time_statistics_api = client.taskrouter_v1_task_queue_real_time_statistics
```

## Class Name

`TaskrouterV1TaskQueueRealTimeStatisticsApi`


# Fetch Task Queue Real Time Statistics

```ruby
def fetch_task_queue_real_time_statistics(workspace_sid,
                                          task_queue_sid,
                                          task_channel: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the TaskQueue to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `task_queue_sid` | `String` | Template, Required | The SID of the TaskQueue for which to fetch statistics.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `task_channel` | `String` | Query, Optional | The TaskChannel for which to fetch statistics. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`TaskQueueRealTimeStatistics`](../../doc/models/task-queue-real-time-statistics.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

task_queue_sid = 'TaskQueueSid8'

task_channel = 'voice'

result = taskrouter_v1_task_queue_real_time_statistics_api.fetch_task_queue_real_time_statistics(
  workspace_sid,
  task_queue_sid,
  task_channel: task_channel
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

