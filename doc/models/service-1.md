
# Service 1

*This model accepts additional fields of type Object.*

## Structure

`Service1`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | The unique string that we created to identify the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Optional | The string that you assigned to describe the resource. |
| `date_created` | `DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `date_updated` | `DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `apn_credential_sid` | `String` | Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for APN Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `gcm_credential_sid` | `String` | Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for GCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `fcm_credential_sid` | `String` | Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for FCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `messaging_service_sid` | `String` | Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/sms/quickstart#messaging-services) to use for SMS Bindings. In order to send SMS notifications this parameter has to be set.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `facebook_messenger_page_id` | `String` | Optional | Deprecated. |
| `default_apn_notification_protocol_version` | `String` | Optional | The protocol version to use for sending APNS notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `default_gcm_notification_protocol_version` | `String` | Optional | The protocol version to use for sending GCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `default_fcm_notification_protocol_version` | `String` | Optional | The protocol version to use for sending FCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `log_enabled` | `TrueClass \| FalseClass` | Optional | Whether to log notifications. Can be: `true` or `false` and the default is `true`. |
| `url` | `String` | Optional | The absolute URL of the Service resource. |
| `links` | `Object` | Optional | The URLs of the Binding, Notification, Segment, and User resources related to the service. |
| `alexa_skill_id` | `String` | Optional | Deprecated. |
| `default_alexa_notification_protocol_version` | `String` | Optional | Deprecated. |
| `delivery_callback_url` | `String` | Optional | URL to send delivery status callback. |
| `delivery_callback_enabled` | `TrueClass \| FalseClass` | Optional | Callback configuration that enables delivery callbacks, default false |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "account_sid": "account_sid6",
  "friendly_name": "friendly_name6",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

