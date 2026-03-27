# Taskrouter V1 Workflow

```ruby
taskrouter_v1_workflow_api = client.taskrouter_v1_workflow
```

## Class Name

`TaskrouterV1WorkflowApi`

## Methods

* [Fetch Workflow](../../doc/controllers/taskrouter-v1-workflow.md#fetch-workflow)
* [Update Workflow](../../doc/controllers/taskrouter-v1-workflow.md#update-workflow)
* [Delete Workflow](../../doc/controllers/taskrouter-v1-workflow.md#delete-workflow)
* [List Workflow](../../doc/controllers/taskrouter-v1-workflow.md#list-workflow)
* [Create Workflow](../../doc/controllers/taskrouter-v1-workflow.md#create-workflow)


# Fetch Workflow

```ruby
def fetch_workflow(workspace_sid,
                   sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Workflow to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Workflow resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Workflow`](../../doc/models/workflow.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

sid = 'Sid8'

result = taskrouter_v1_workflow_api.fetch_workflow(
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
  "assignment_callback_url": "http://example.com",
  "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "document_content_type": "application/json",
  "fallback_assignment_callback_url": null,
  "friendly_name": "Default Fifo Workflow",
  "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_reservation_timeout": 120,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
  }
}
```


# Update Workflow

```ruby
def update_workflow(workspace_sid,
                    sid,
                    friendly_name: nil,
                    assignment_callback_url: nil,
                    fallback_assignment_callback_url: nil,
                    configuration: nil,
                    task_reservation_timeout: nil,
                    re_evaluate_tasks: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Workflow to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Workflow resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Form, Optional | A descriptive string that you create to describe the Workflow resource. For example, `Inbound Call Workflow` or `2014 Outbound Campaign`. |
| `assignment_callback_url` | `String` | Form, Optional | The URL from your application that will process task assignment events. See [Handling Task Assignment Callback](https://www.twilio.com/docs/taskrouter/handle-assignment-callbacks) for more details. |
| `fallback_assignment_callback_url` | `String` | Form, Optional | The URL that we should call when a call to the `assignment_callback_url` fails. |
| `configuration` | `String` | Form, Optional | A JSON string that contains the rules to apply to the Workflow. See [Configuring Workflows](https://www.twilio.com/docs/taskrouter/workflow-configuration) for more information. |
| `task_reservation_timeout` | `Integer` | Form, Optional | How long TaskRouter will wait for a confirmation response from your application after it assigns a Task to a Worker. Can be up to `86,400` (24 hours) and the default is `120`. |
| `re_evaluate_tasks` | `String` | Form, Optional | Whether or not to re-evaluate Tasks. The default is `false`, which means Tasks in the Workflow will not be processed through the assignment loop again. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Workflow`](../../doc/models/workflow.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

sid = 'Sid8'

friendly_name = 'friendly_name'

assignment_callback_url = 'http://example.com'

fallback_assignment_callback_url = 'http://example.com'

configuration = 'configuration'

task_reservation_timeout = 1

re_evaluate_tasks = 'false'

result = taskrouter_v1_workflow_api.update_workflow(
  workspace_sid,
  sid,
  friendly_name: friendly_name,
  assignment_callback_url: assignment_callback_url,
  fallback_assignment_callback_url: fallback_assignment_callback_url,
  configuration: configuration,
  task_reservation_timeout: task_reservation_timeout,
  re_evaluate_tasks: re_evaluate_tasks
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
  "assignment_callback_url": "http://example.com",
  "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "document_content_type": "application/json",
  "fallback_assignment_callback_url": null,
  "friendly_name": "Default Fifo Workflow",
  "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_reservation_timeout": 120,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
  },
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Workflow

```ruby
def delete_workflow(workspace_sid,
                    sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Workflow to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Workflow resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

sid = 'Sid8'

result = taskrouter_v1_workflow_api.delete_workflow(
  workspace_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# List Workflow

```ruby
def list_workflow(workspace_sid,
                  friendly_name: nil,
                  page_size: nil,
                  page: nil,
                  page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the Workflow to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Query, Optional | The `friendly_name` of the Workflow resources to read. |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListWorkflowResponse`](../../doc/models/list-workflow-response.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

friendly_name = 'friendly_name'

result = taskrouter_v1_workflow_api.list_workflow(
  workspace_sid,
  friendly_name: friendly_name
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
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows?FriendlyName=friendly_name&PageSize=50&Page=0",
    "key": "workflows",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows?FriendlyName=friendly_name&PageSize=50&Page=0"
  },
  "workflows": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "assignment_callback_url": "http://example.com",
      "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
      "date_created": "2014-05-14T10:50:02Z",
      "date_updated": "2014-05-15T16:47:51Z",
      "document_content_type": "application/json",
      "fallback_assignment_callback_url": null,
      "friendly_name": "Default Fifo Workflow",
      "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_reservation_timeout": 120,
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
        "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
        "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
      },
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Create Workflow

```ruby
def create_workflow(workspace_sid,
                    friendly_name,
                    configuration,
                    assignment_callback_url: nil,
                    fallback_assignment_callback_url: nil,
                    task_reservation_timeout: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace that the new Workflow to create belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Form, Required | A descriptive string that you create to describe the Workflow resource. For example, `Inbound Call Workflow` or `2014 Outbound Campaign`. |
| `configuration` | `String` | Form, Required | A JSON string that contains the rules to apply to the Workflow. See [Configuring Workflows](https://www.twilio.com/docs/taskrouter/workflow-configuration) for more information. |
| `assignment_callback_url` | `String` | Form, Optional | The URL from your application that will process task assignment events. See [Handling Task Assignment Callback](https://www.twilio.com/docs/taskrouter/handle-assignment-callbacks) for more details. |
| `fallback_assignment_callback_url` | `String` | Form, Optional | The URL that we should call when a call to the `assignment_callback_url` fails. |
| `task_reservation_timeout` | `Integer` | Form, Optional | How long TaskRouter will wait for a confirmation response from your application after it assigns a Task to a Worker. Can be up to `86,400` (24 hours) and the default is `120`. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Workflow`](../../doc/models/workflow.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

friendly_name = 'friendly_name'

configuration = 'configuration'

assignment_callback_url = 'http://example.com'

fallback_assignment_callback_url = 'http://example.com'

task_reservation_timeout = 1

result = taskrouter_v1_workflow_api.create_workflow(
  workspace_sid,
  friendly_name,
  configuration,
  assignment_callback_url: assignment_callback_url,
  fallback_assignment_callback_url: fallback_assignment_callback_url,
  task_reservation_timeout: task_reservation_timeout
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
  "assignment_callback_url": "http://example.com",
  "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "document_content_type": "application/json",
  "fallback_assignment_callback_url": null,
  "friendly_name": "Default Fifo Workflow",
  "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_reservation_timeout": 120,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
  }
}
```

