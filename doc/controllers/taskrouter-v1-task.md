# Taskrouter V1 Task

```ruby
taskrouter_v1_task_api = client.taskrouter_v1_task
```

## Class Name

`TaskrouterV1TaskApi`

## Methods

* [Fetch Task](../../doc/controllers/taskrouter-v1-task.md#fetch-task)
* [Update Task](../../doc/controllers/taskrouter-v1-task.md#update-task)
* [Delete Task](../../doc/controllers/taskrouter-v1-task.md#delete-task)
* [List Task](../../doc/controllers/taskrouter-v1-task.md#list-task)
* [Create Task](../../doc/controllers/taskrouter-v1-task.md#create-task)


# Fetch Task

```ruby
def fetch_task(workspace_sid,
               sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Task to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Task resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`TaskRouterTask`](../../doc/models/task-router-task.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

sid = 'Sid8'

result = taskrouter_v1_task_api.fetch_task(
  workspace_sid,
  sid
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
  "age": 25200,
  "assignment_status": "pending",
  "attributes": "{\"body\": \"hello\"}",
  "date_created": "2014-05-14T18:50:02Z",
  "date_updated": "2014-05-15T07:26:06Z",
  "task_queue_entered_date": "2014-05-14T18:50:02Z",
  "virtual_start_time": "2014-05-14T18:50:02Z",
  "priority": 0,
  "reason": "Test Reason",
  "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_unique_name": "task-channel",
  "timeout": 60,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_friendly_name": "Test Workflow",
  "task_queue_friendly_name": "Test Queue",
  "ignore_capacity": false,
  "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "addons": "{}",
  "links": {
    "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```


# Update Task

```ruby
def update_task(workspace_sid,
                sid,
                if_match: nil,
                attributes: nil,
                assignment_status: nil,
                reason: nil,
                priority: nil,
                task_channel: nil,
                virtual_start_time: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Task to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Task resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `if_match` | `String` | Header, Optional | If provided, applies this mutation if (and only if) the [ETag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag) header of the Task matches the provided value. This matches the semantics of (and is implemented with) the HTTP [If-Match header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-Match). |
| `attributes` | `String` | Form, Optional | The JSON string that describes the custom attributes of the task. |
| `assignment_status` | [`TaskStatus`](../../doc/models/task-status.md) | Form, Optional | The current status of the Task's assignment. Can be: `pending`, `reserved`, `assigned`, `canceled`, `wrapping`, or `completed`. |
| `reason` | `String` | Form, Optional | The reason that the Task was canceled or completed. This parameter is required only if the Task is canceled or completed. Setting this value queues the task for deletion and logs the reason. |
| `priority` | `Integer` | Form, Optional | The Task's new priority value. When supplied, the Task takes on the specified priority unless it matches a Workflow Target with a Priority set. Value can be 0 to 2^31^ (2,147,483,647). |
| `task_channel` | `String` | Form, Optional | When MultiTasking is enabled, specify the TaskChannel with the task to update. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `virtual_start_time` | `DateTime` | Form, Optional | The task's new virtual start time value. When supplied, the Task takes on the specified virtual start time. Value can't be in the future or before the year of 1900. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`TaskRouterTask`](../../doc/models/task-router-task.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

sid = 'Sid8'

attributes = 'attributes'

assignment_status = TaskStatus::PENDING

reason = 'reason'

priority = 1

virtual_start_time = DateTimeHelper.from_rfc3339('08/02/2023 12:34:56')

result = taskrouter_v1_task_api.update_task(
  workspace_sid,
  sid,
  attributes: attributes,
  assignment_status: assignment_status,
  reason: reason,
  priority: priority,
  virtual_start_time: virtual_start_time
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
  "age": 25200,
  "assignment_status": "pending",
  "attributes": "{\"body\": \"hello\"}",
  "date_created": "2014-05-14T18:50:02Z",
  "date_updated": "2014-05-15T07:26:06Z",
  "task_queue_entered_date": "2014-05-14T18:50:02Z",
  "virtual_start_time": "2023-08-02T12:34:56Z",
  "priority": 0,
  "reason": "Test Reason",
  "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_unique_name": "task-channel",
  "timeout": 60,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_friendly_name": "Test Workflow",
  "task_queue_friendly_name": "Test Queue",
  "addons": "{}",
  "ignore_capacity": false,
  "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```


# Delete Task

```ruby
def delete_task(workspace_sid,
                sid,
                if_match: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Task to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Task resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `if_match` | `String` | Header, Optional | If provided, deletes this Task if (and only if) the [ETag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag) header of the Task matches the provided value. This matches the semantics of (and is implemented with) the HTTP [If-Match header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-Match). |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

sid = 'Sid8'

result = taskrouter_v1_task_api.delete_task(
  workspace_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Task

```ruby
def list_task(workspace_sid,
              priority: nil,
              assignment_status: nil,
              workflow_sid: nil,
              workflow_name: nil,
              task_queue_sid: nil,
              task_queue_name: nil,
              evaluate_task_attributes: nil,
              routing_target: nil,
              ordering: nil,
              has_addons: nil,
              page_size: nil,
              page: nil,
              page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Tasks to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `priority` | `Integer` | Query, Optional | The priority value of the Tasks to read. Returns the list of all Tasks in the Workspace with the specified priority. |
| `assignment_status` | `Array[String]` | Query, Optional | The `assignment_status` of the Tasks you want to read. Can be: `pending`, `reserved`, `assigned`, `canceled`, `wrapping`, or `completed`. Returns all Tasks in the Workspace with the specified `assignment_status`. |
| `workflow_sid` | `String` | Query, Optional | The SID of the Workflow with the Tasks to read. Returns the Tasks controlled by the Workflow identified by this SID.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `workflow_name` | `String` | Query, Optional | The friendly name of the Workflow with the Tasks to read. Returns the Tasks controlled by the Workflow identified by this friendly name. |
| `task_queue_sid` | `String` | Query, Optional | The SID of the TaskQueue with the Tasks to read. Returns the Tasks waiting in the TaskQueue identified by this SID.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `task_queue_name` | `String` | Query, Optional | The `friendly_name` of the TaskQueue with the Tasks to read. Returns the Tasks waiting in the TaskQueue identified by this friendly name. |
| `evaluate_task_attributes` | `String` | Query, Optional | The attributes of the Tasks to read. Returns the Tasks that match the attributes specified in this parameter. |
| `routing_target` | `String` | Query, Optional | A SID of a Worker, Queue, or Workflow to route a Task to |
| `ordering` | `String` | Query, Optional | How to order the returned Task resources. By default, Tasks are sorted by ascending DateCreated. This value is specified as: `Attribute:Order`, where `Attribute` can be either `DateCreated`, `Priority`, or `VirtualStartTime` and `Order` can be either `asc` or `desc`. For example, `Priority:desc` returns Tasks ordered in descending order of their Priority. Pairings of sort orders can be specified in a comma-separated list such as `Priority:desc,DateCreated:asc`, which returns the Tasks in descending Priority order and ascending DateCreated Order. The only ordering pairing not allowed is DateCreated and VirtualStartTime. |
| `has_addons` | `TrueClass \| FalseClass` | Query, Optional | Whether to read Tasks with Add-ons. If `true`, returns only Tasks with Add-ons. If `false`, returns only Tasks without Add-ons. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListTaskResponse`](../../doc/models/list-task-response.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

priority = 1

assignment_status = [
  'pending',
  'reserved'
]

workflow_sid = 'WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

workflow_name = 'workflow_name'

task_queue_sid = 'WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

task_queue_name = 'task_queue_name'

routing_target = 'WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = taskrouter_v1_task_api.list_task(
  workspace_sid,
  priority: priority,
  assignment_status: assignment_status,
  workflow_sid: workflow_sid,
  workflow_name: workflow_name,
  task_queue_sid: task_queue_sid,
  task_queue_name: task_queue_name,
  routing_target: routing_target
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
  "meta": {
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks?TaskQueueSid=WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&RoutingTarget=WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&TaskQueueName=task_queue_name&WorkflowName=workflow_name&WorkflowSid=WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&AssignmentStatus=pending%2Creserved&Priority=1&PageSize=50&Page=0",
    "key": "tasks",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks?TaskQueueSid=WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&RoutingTarget=WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&TaskQueueName=task_queue_name&WorkflowName=workflow_name&WorkflowSid=WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&AssignmentStatus=pending%2Creserved&Priority=1&PageSize=50&Page=0"
  },
  "tasks": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "age": 25200,
      "assignment_status": "pending",
      "attributes": "{\"body\": \"hello\"}",
      "date_created": "2014-05-14T14:26:54Z",
      "date_updated": "2014-05-15T16:03:42Z",
      "task_queue_entered_date": "2014-05-14T14:26:54Z",
      "virtual_start_time": "2014-05-14T14:26:54Z",
      "priority": 0,
      "reason": "Test Reason",
      "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_channel_unique_name": "task-channel",
      "timeout": 60,
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workflow_friendly_name": "Test Workflow",
      "task_queue_friendly_name": "Test Queue",
      "ignore_capacity": false,
      "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "addons": "{}",
      "links": {
        "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
      }
    }
  ]
}
```


# Create Task

```ruby
def create_task(workspace_sid,
                timeout: nil,
                priority: nil,
                task_channel: nil,
                workflow_sid: nil,
                attributes: nil,
                virtual_start_time: nil,
                routing_target: nil,
                ignore_capacity: nil,
                task_queue_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace that the new Task belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `timeout` | `Integer` | Form, Optional | The amount of time in seconds the new task can live before being assigned. Can be up to a maximum of 2 weeks (1,209,600 seconds). The default value is 24 hours (86,400 seconds). On timeout, the `task.canceled` event will fire with description `Task TTL Exceeded`. |
| `priority` | `Integer` | Form, Optional | The priority to assign the new task and override the default. When supplied, the new Task will have this priority unless it matches a Workflow Target with a Priority set. When not supplied, the new Task will have the priority of the matching Workflow Target. Value can be 0 to 2^31^ (2,147,483,647). |
| `task_channel` | `String` | Form, Optional | When MultiTasking is enabled, specify the TaskChannel by passing either its `unique_name` or `sid`. Default value is `default`. |
| `workflow_sid` | `String` | Form, Optional | The SID of the Workflow that you would like to handle routing for the new Task. If there is only one Workflow defined for the Workspace that you are posting the new task to, this parameter is optional.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `attributes` | `String` | Form, Optional | A JSON string with the attributes of the new task. This value is passed to the Workflow's `assignment_callback_url` when the Task is assigned to a Worker. For example: `{ "task_type": "call", "twilio_call_sid": "CAxxx", "customer_ticket_number": "12345" }`. |
| `virtual_start_time` | `DateTime` | Form, Optional | The virtual start time to assign the new task and override the default. When supplied, the new task will have this virtual start time. When not supplied, the new task will have the virtual start time equal to `date_created`. Value can't be in the future or before the year of 1900. |
| `routing_target` | `String` | Form, Optional | A SID of a Worker, Queue, or Workflow to route a Task to |
| `ignore_capacity` | `String` | Form, Optional | A boolean that indicates if the Task should respect a Worker's capacity and availability during assignment. This field can only be used when the `RoutingTarget` field is set to a Worker SID. By setting `IgnoreCapacity` to a value of `true`, `1`, or `yes`, the Task will be routed to the Worker without respecting their capacity and availability. Any other value will enforce the Worker's capacity and availability. The default value of `IgnoreCapacity` is `true` when the `RoutingTarget` is set to a Worker SID. |
| `task_queue_sid` | `String` | Form, Optional | The SID of the TaskQueue in which the Task belongs<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`TaskRouterTask`](../../doc/models/task-router-task.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

timeout = 1

priority = 1

task_channel = 'channel'

workflow_sid = 'WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

attributes = '{"body": "attributes"}'

virtual_start_time = DateTimeHelper.from_rfc3339('05/14/2014 18:50:02')

routing_target = 'WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

ignore_capacity = 'false'

task_queue_sid = 'WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = taskrouter_v1_task_api.create_task(
  workspace_sid,
  timeout: timeout,
  priority: priority,
  task_channel: task_channel,
  workflow_sid: workflow_sid,
  attributes: attributes,
  virtual_start_time: virtual_start_time,
  routing_target: routing_target,
  ignore_capacity: ignore_capacity,
  task_queue_sid: task_queue_sid
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
  "age": 25200,
  "assignment_status": "pending",
  "attributes": "{\"body\": \"attributes\"}",
  "date_created": "2014-05-14T18:50:02Z",
  "date_updated": "2014-05-15T07:26:06Z",
  "task_queue_entered_date": null,
  "virtual_start_time": "2014-05-14T18:50:02Z",
  "priority": 1,
  "reason": "Test Reason",
  "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_unique_name": "unique",
  "timeout": 60,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_friendly_name": "Example Workflow",
  "task_queue_friendly_name": "Example Task Queue",
  "ignore_capacity": false,
  "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "addons": "{}",
  "links": {
    "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```

