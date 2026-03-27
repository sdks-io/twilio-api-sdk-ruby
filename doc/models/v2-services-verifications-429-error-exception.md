
# V2 Services Verifications 429 Error Exception

*This model accepts additional fields of type Object.*

## Structure

`V2ServicesVerifications429ErrorException`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `code` | `Integer` | Optional | Twilio-specific error code |
| `message` | `String` | Optional | Error message |
| `more_info` | `String` | Optional | Link to Error Code References |
| `status` | `Integer` | Optional | HTTP response status code |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "code": 0,
  "message": "message0",
  "more_info": "more_info2",
  "status": 178,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

