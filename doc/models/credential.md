
# Credential

*This model accepts additional fields of type Object.*

## Structure

`Credential`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this credential.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Optional | The human-readable name of this credential, limited to 64 characters. Optional. |
| `type` | [`CredentialPushType`](../../doc/models/credential-push-type.md) | Optional | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. |
| `sandbox` | `String` | Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `date_created` | `DateTime` | Optional | The date that this resource was created. |
| `date_updated` | `DateTime` | Optional | The date that this resource was last updated. |
| `url` | `String` | Optional | An absolute API resource URL for this credential. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "account_sid": "account_sid6",
  "friendly_name": "friendly_name6",
  "type": "gcm",
  "sandbox": "sandbox8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

