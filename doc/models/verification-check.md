
# Verification Check

*This model accepts additional fields of type Object.*

## Structure

`VerificationCheck`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | The unique string that we created to identify the VerificationCheck resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VE[0-9a-fA-F]{32}$` |
| `service_sid` | `String` | Optional | The SID of the [Service](https://www.twilio.com/docs/verify/api/service) the resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the VerificationCheck resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `to` | `String` | Optional | The phone number or [email](https://www.twilio.com/docs/verify/email) being verified. Phone numbers must be in [E.164 format](https://www.twilio.com/docs/glossary/what-e164). |
| `channel` | [`VerificationCheckEnumChannel`](../../doc/models/verification-check-enum-channel.md) | Optional | The verification method to use. One of: [`email`](https://www.twilio.com/docs/verify/email), `sms`, `whatsapp`, `call`, or `sna`. |
| `status` | `String` | Optional | The status of the verification. Can be: `pending`, `approved`, `canceled`, `max_attempts_reached`, `deleted`, `failed` or `expired`. |
| `valid` | `TrueClass \| FalseClass` | Optional | Use "status" instead. Legacy property indicating whether the verification was successful. |
| `amount` | `String` | Optional | The amount of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. |
| `payee` | `String` | Optional | The payee of the associated PSD2 compliant transaction. Requires the PSD2 Service flag enabled. |
| `date_created` | `DateTime` | Optional | The [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date and time in GMT when the Verification Check resource was created. |
| `date_updated` | `DateTime` | Optional | The [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date and time in GMT when the Verification Check resource was last updated. |
| `sna_attempts_error_codes` | `Array[Object]` | Optional | List of error codes as a result of attempting a verification using the `sna` channel. The error codes are chronologically ordered, from the first attempt to the latest attempt. This will be an empty list if no errors occured or `null` if the last channel used wasn't `sna`. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "service_sid": "service_sid2",
  "account_sid": "account_sid6",
  "to": "to6",
  "channel": "sna",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

