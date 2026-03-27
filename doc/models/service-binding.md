
# Service Binding

*This model accepts additional fields of type Object.*

## Structure

`ServiceBinding`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this binding.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `chat_service_sid` | `String` | Optional | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Binding resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `credential_sid` | `String` | Optional | The SID of the [Credential](https://www.twilio.com/docs/conversations/api/credential-resource) for the binding. See [push notification configuration](https://www.twilio.com/docs/chat/push-notification-configuration) for more info.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `date_created` | `DateTime` | Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Optional | The date that this resource was last updated. |
| `endpoint` | `String` | Optional | The unique endpoint identifier for the Binding. The format of this value depends on the `binding_type`. |
| `identity` | `String` | Optional | The application-defined string that uniquely identifies the [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource) within the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource). See [access tokens](https://www.twilio.com/docs/conversations/create-tokens) for more info. |
| `binding_type` | [`ServiceBindingBindingType`](../../doc/models/service-binding-binding-type.md) | Optional | The push technology to use for the Binding. Can be: `apn`, `gcm`, `fcm`, or `twilsock`.  See [push notification configuration](https://www.twilio.com/docs/chat/push-notification-configuration) for more info. |
| `message_types` | `Array[String]` | Optional | The [Conversation message types](https://www.twilio.com/docs/chat/push-notification-configuration#push-types) the binding is subscribed to. |
| `url` | `String` | Optional | An absolute API resource URL for this binding. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid4",
  "account_sid": "account_sid8",
  "chat_service_sid": "chat_service_sid2",
  "credential_sid": "credential_sid2",
  "date_created": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

