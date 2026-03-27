# Taskrouter V1 Task Reservation

```ruby
taskrouter_v1_task_reservation_api = client.taskrouter_v1_task_reservation
```

## Class Name

`TaskrouterV1TaskReservationApi`

## Methods

* [List Task Reservation](../../doc/controllers/taskrouter-v1-task-reservation.md#list-task-reservation)
* [Fetch Task Reservation](../../doc/controllers/taskrouter-v1-task-reservation.md#fetch-task-reservation)
* [Update Task Reservation](../../doc/controllers/taskrouter-v1-task-reservation.md#update-task-reservation)


# List Task Reservation

Tasks reserved for workers

```ruby
def list_task_reservation(workspace_sid,
                          task_sid,
                          reservation_status: nil,
                          worker_sid: nil,
                          page_size: nil,
                          page: nil,
                          page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the TaskReservation resources to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `task_sid` | `String` | Template, Required | The SID of the reserved Task resource with the TaskReservation resources to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `reservation_status` | [`TaskReservationStatus`](../../doc/models/task-reservation-status.md) | Query, Optional | Returns the list of reservations for a task with a specified ReservationStatus.  Can be: `pending`, `accepted`, `rejected`, or `timeout`. |
| `worker_sid` | `String` | Query, Optional | The SID of the reserved Worker resource to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListTaskReservationResponse`](../../doc/models/list-task-reservation-response.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

task_sid = 'TaskSid8'

result = taskrouter_v1_task_reservation_api.list_task_reservation(
  workspace_sid,
  task_sid
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
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations?PageSize=50&Page=0",
    "key": "reservations",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations?PageSize=50&Page=0"
  },
  "reservations": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2014-05-14T10:50:02Z",
      "date_updated": "2014-05-15T16:03:42Z",
      "links": {
        "task": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "worker": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
      },
      "reservation_status": "accepted",
      "sid": "WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations/WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "worker_name": "Doug",
      "worker_sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Fetch Task Reservation

Tasks reserved for workers

```ruby
def fetch_task_reservation(workspace_sid,
                           task_sid,
                           sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the TaskReservation resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `task_sid` | `String` | Template, Required | The SID of the reserved Task resource with the TaskReservation resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the TaskReservation resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WR[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`TaskReservation`](../../doc/models/task-reservation.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

task_sid = 'TaskSid8'

sid = 'Sid8'

result = taskrouter_v1_task_reservation_api.fetch_task_reservation(
  workspace_sid,
  task_sid,
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
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-15T16:03:42Z",
  "links": {
    "task": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "worker": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  },
  "reservation_status": "accepted",
  "sid": "WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations/WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "worker_name": "Doug",
  "worker_sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Task Reservation

Tasks reserved for workers

```ruby
def update_task_reservation(workspace_sid,
                            task_sid,
                            sid,
                            if_match: nil,
                            reservation_status: nil,
                            worker_activity_sid: nil,
                            instruction: nil,
                            dequeue_post_work_activity_sid: nil,
                            dequeue_from: nil,
                            dequeue_record: nil,
                            dequeue_timeout: nil,
                            dequeue_to: nil,
                            dequeue_status_callback_url: nil,
                            call_from: nil,
                            call_record: nil,
                            call_timeout: nil,
                            call_to: nil,
                            call_url: nil,
                            call_status_callback_url: nil,
                            call_accept: nil,
                            redirect_call_sid: nil,
                            redirect_accept: nil,
                            redirect_url: nil,
                            to: nil,
                            from: nil,
                            status_callback: nil,
                            status_callback_method: nil,
                            status_callback_event: nil,
                            timeout: nil,
                            record: nil,
                            muted: nil,
                            beep: nil,
                            start_conference_on_enter: nil,
                            end_conference_on_exit: nil,
                            wait_url: nil,
                            wait_method: nil,
                            early_media: nil,
                            max_participants: nil,
                            conference_status_callback: nil,
                            conference_status_callback_method: nil,
                            conference_status_callback_event: nil,
                            conference_record: nil,
                            conference_trim: nil,
                            recording_channels: nil,
                            recording_status_callback: nil,
                            recording_status_callback_method: nil,
                            conference_recording_status_callback: nil,
                            conference_recording_status_callback_method: nil,
                            region: nil,
                            sip_auth_username: nil,
                            sip_auth_password: nil,
                            dequeue_status_callback_event: nil,
                            post_work_activity_sid: nil,
                            supervisor_mode: nil,
                            supervisor: nil,
                            end_conference_on_customer_exit: nil,
                            beep_on_customer_entrance: nil,
                            jitter_buffer_size: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspace_sid` | `String` | Template, Required | The SID of the Workspace with the TaskReservation resources to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `task_sid` | `String` | Template, Required | The SID of the reserved Task resource with the TaskReservation resources to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the TaskReservation resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WR[0-9a-fA-F]{32}$` |
| `if_match` | `String` | Header, Optional | The If-Match HTTP request header |
| `reservation_status` | [`TaskReservationStatus`](../../doc/models/task-reservation-status.md) | Form, Optional | The current status of the reservation. Can be: `pending`, `accepted`, `rejected`, or `timeout`. |
| `worker_activity_sid` | `String` | Form, Optional | The new worker activity SID if rejecting a reservation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `instruction` | `String` | Form, Optional | The assignment instruction for reservation. |
| `dequeue_post_work_activity_sid` | `String` | Form, Optional | The SID of the Activity resource to start after executing a Dequeue instruction.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `dequeue_from` | `String` | Form, Optional | The Caller ID of the call to the worker when executing a Dequeue instruction. |
| `dequeue_record` | `String` | Form, Optional | Whether to record both legs of a call when executing a Dequeue instruction or which leg to record. |
| `dequeue_timeout` | `Integer` | Form, Optional | Timeout for call when executing a Dequeue instruction. |
| `dequeue_to` | `String` | Form, Optional | The Contact URI of the worker when executing a Dequeue instruction. Can be the URI of the Twilio Client, the SIP URI for Programmable SIP, or the [E.164](https://www.twilio.com/docs/glossary/what-e164) formatted phone number, depending on the destination. |
| `dequeue_status_callback_url` | `String` | Form, Optional | The Callback URL for completed call event when executing a Dequeue instruction. |
| `call_from` | `String` | Form, Optional | The Caller ID of the outbound call when executing a Call instruction. |
| `call_record` | `String` | Form, Optional | Whether to record both legs of a call when executing a Call instruction or which leg to record. |
| `call_timeout` | `Integer` | Form, Optional | Timeout for call when executing a Call instruction. |
| `call_to` | `String` | Form, Optional | The Contact URI of the worker when executing a Call instruction.  Can be the URI of the Twilio Client, the SIP URI for Programmable SIP, or the [E.164](https://www.twilio.com/docs/glossary/what-e164) formatted phone number, depending on the destination. |
| `call_url` | `String` | Form, Optional | TwiML URI executed on answering the worker's leg as a result of the Call instruction. |
| `call_status_callback_url` | `String` | Form, Optional | The URL to call  for the completed call event when executing a Call instruction. |
| `call_accept` | `TrueClass \| FalseClass` | Form, Optional | Whether to accept a reservation when executing a Call instruction. |
| `redirect_call_sid` | `String` | Form, Optional | The Call SID of the call parked in the queue when executing a Redirect instruction.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CA[0-9a-fA-F]{32}$` |
| `redirect_accept` | `TrueClass \| FalseClass` | Form, Optional | Whether the reservation should be accepted when executing a Redirect instruction. |
| `redirect_url` | `String` | Form, Optional | TwiML URI to redirect the call to when executing the Redirect instruction. |
| `to` | `String` | Form, Optional | The Contact URI of the worker when executing a Conference instruction. Can be the URI of the Twilio Client, the SIP URI for Programmable SIP, or the [E.164](https://www.twilio.com/docs/glossary/what-e164) formatted phone number, depending on the destination. |
| `from` | `String` | Form, Optional | The Caller ID of the call to the worker when executing a Conference instruction. |
| `status_callback` | `String` | Form, Optional | The URL we should call using the `status_callback_method` to send status information to your application. |
| `status_callback_method` | [`ConfigurationWebhookMethod`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `status_callback`. Can be: `POST` or `GET` and the default is `POST`. |
| `status_callback_event` | [`Array[TaskReservationCallStatus]`](../../doc/models/task-reservation-call-status.md) | Form, Optional | The call progress events that we will send to `status_callback`. Can be: `initiated`, `ringing`, `answered`, or `completed`. |
| `timeout` | `Integer` | Form, Optional | Timeout for call when executing a Conference instruction. |
| `record` | `TrueClass \| FalseClass` | Form, Optional | Whether to record the participant and their conferences, including the time between conferences. The default is `false`. |
| `muted` | `TrueClass \| FalseClass` | Form, Optional | Whether the agent is muted in the conference. The default is `false`. |
| `beep` | `String` | Form, Optional | Whether to play a notification beep when the participant joins or when to play a beep. Can be: `true`, `false`, `onEnter`, or `onExit`. The default value is `true`. |
| `start_conference_on_enter` | `TrueClass \| FalseClass` | Form, Optional | Whether to start the conference when the participant joins, if it has not already started. The default is `true`. If `false` and the conference has not started, the participant is muted and hears background music until another participant starts the conference. |
| `end_conference_on_exit` | `TrueClass \| FalseClass` | Form, Optional | Whether to end the conference when the agent leaves. |
| `wait_url` | `String` | Form, Optional | The URL we should call using the `wait_method` for the music to play while participants are waiting for the conference to start. The default value is the URL of our standard hold music. [Learn more about hold music](https://www.twilio.com/labs/twimlets/holdmusic). |
| `wait_method` | [`ConfigurationWebhookMethod`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `wait_url`. Can be `GET` or `POST` and the default is `POST`. When using a static audio file, this should be `GET` so that we can cache the file. |
| `early_media` | `TrueClass \| FalseClass` | Form, Optional | Whether to allow an agent to hear the state of the outbound call, including ringing or disconnect messages. The default is `true`. |
| `max_participants` | `Integer` | Form, Optional | The maximum number of participants in the conference. Can be a positive integer from `2` to `250`. The default value is `250`. |
| `conference_status_callback` | `String` | Form, Optional | The URL we should call using the `conference_status_callback_method` when the conference events in `conference_status_callback_event` occur. Only the value set by the first participant to join the conference is used. Subsequent `conference_status_callback` values are ignored. |
| `conference_status_callback_method` | [`ConfigurationWebhookMethod`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `conference_status_callback`. Can be: `GET` or `POST` and defaults to `POST`. |
| `conference_status_callback_event` | [`Array[TaskReservationConferenceEvent]`](../../doc/models/task-reservation-conference-event.md) | Form, Optional | The conference status events that we will send to `conference_status_callback`. Can be: `start`, `end`, `join`, `leave`, `mute`, `hold`, `speaker`. |
| `conference_record` | `String` | Form, Optional | Whether to record the conference the participant is joining or when to record the conference. Can be: `true`, `false`, `record-from-start`, and `do-not-record`. The default value is `false`. |
| `conference_trim` | `String` | Form, Optional | How to trim the leading and trailing silence from your recorded conference audio files. Can be: `trim-silence` or `do-not-trim` and defaults to `trim-silence`. |
| `recording_channels` | `String` | Form, Optional | The recording channels for the final recording. Can be: `mono` or `dual` and the default is `mono`. |
| `recording_status_callback` | `String` | Form, Optional | The URL that we should call using the `recording_status_callback_method` when the recording status changes. |
| `recording_status_callback_method` | [`ConfigurationWebhookMethod`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use when we call `recording_status_callback`. Can be: `GET` or `POST` and defaults to `POST`. |
| `conference_recording_status_callback` | `String` | Form, Optional | The URL we should call using the `conference_recording_status_callback_method` when the conference recording is available. |
| `conference_recording_status_callback_method` | [`ConfigurationWebhookMethod`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `conference_recording_status_callback`. Can be: `GET` or `POST` and defaults to `POST`. |
| `region` | `String` | Form, Optional | The [region](https://support.twilio.com/hc/en-us/articles/223132167-How-global-low-latency-routing-and-region-selection-work-for-conferences-and-Client-calls) where we should mix the recorded audio. Can be:`us1`, `us2`, `ie1`, `de1`, `sg1`, `br1`, `au1`, or `jp1`. |
| `sip_auth_username` | `String` | Form, Optional | The SIP username used for authentication. |
| `sip_auth_password` | `String` | Form, Optional | The SIP password for authentication. |
| `dequeue_status_callback_event` | `Array[String]` | Form, Optional | The Call progress events sent via webhooks as a result of a Dequeue instruction. |
| `post_work_activity_sid` | `String` | Form, Optional | The new worker activity SID after executing a Conference instruction.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `supervisor_mode` | [`TaskReservationSupervisorMode`](../../doc/models/task-reservation-supervisor-mode.md) | Form, Optional | - |
| `supervisor` | `String` | Form, Optional | The Supervisor SID/URI when executing the Supervise instruction. |
| `end_conference_on_customer_exit` | `TrueClass \| FalseClass` | Form, Optional | Whether to end the conference when the customer leaves. |
| `beep_on_customer_entrance` | `TrueClass \| FalseClass` | Form, Optional | Whether to play a notification beep when the customer joins. |
| `jitter_buffer_size` | `String` | Form, Optional | The jitter buffer size for conference. Can be: `small`, `medium`, `large`, `off`. |

## Server

`Server::DEFAULT4`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`TaskReservation`](../../doc/models/task-reservation.md).

## Example Usage

```ruby
workspace_sid = 'WorkspaceSid0'

task_sid = 'TaskSid8'

sid = 'Sid8'

reservation_status = TaskReservationStatus::ACCEPTED

instruction = 'supervise'

supervisor_mode = TaskReservationSupervisorMode::MONITOR

supervisor = 'WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = taskrouter_v1_task_reservation_api.update_task_reservation(
  workspace_sid,
  task_sid,
  sid,
  reservation_status: reservation_status,
  instruction: instruction,
  supervisor_mode: supervisor_mode,
  supervisor: supervisor
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
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-15T16:03:42Z",
  "links": {
    "task": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "worker": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  },
  "reservation_status": "accepted",
  "sid": "WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations/WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "worker_name": "Doug",
  "worker_sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

