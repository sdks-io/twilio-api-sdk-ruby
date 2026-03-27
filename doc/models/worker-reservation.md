
# Worker Reservation

*This model accepts additional fields of type Object.*

## Structure

`WorkerReservation`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the WorkerReservation resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `date_created` | `DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `date_updated` | `DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `reservation_status` | [`WorkerReservationStatus`](../../doc/models/worker-reservation-status.md) | Optional | The current status of the reservation. Can be: `pending`, `accepted`, `rejected`, `timeout`, `canceled`, or `rescinded`. |
| `sid` | `String` | Optional | The unique string that we created to identify the WorkerReservation resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WR[0-9a-fA-F]{32}$` |
| `task_sid` | `String` | Optional | The SID of the reserved Task resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `worker_name` | `String` | Optional | The `friendly_name` of the Worker that is reserved. |
| `worker_sid` | `String` | Optional | The SID of the reserved Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `workspace_sid` | `String` | Optional | The SID of the Workspace that this worker is contained within.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `url` | `String` | Optional | The absolute URL of the WorkerReservation resource. |
| `links` | `Object` | Optional | The URLs of related resources. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "reservation_status": "rejected",
  "sid": "sid0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

