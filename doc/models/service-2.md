
# Service 2

*This model accepts additional fields of type Object.*

## Structure

`Service2`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | The unique string that we created to identify the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^VA[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Service resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Optional | The name that appears in the body of your verification messages. It can be up to 30 characters long and can include letters, numbers, spaces, dashes, underscores. Phone numbers, special characters or links are NOT allowed. It cannot contain more than 4 (consecutive or non-consecutive) digits. **This value should not contain PII.** |
| `code_length` | `Integer` | Optional | The length of the verification code to generate.<br><br>**Default**: `0` |
| `lookup_enabled` | `TrueClass \| FalseClass` | Optional | Whether to perform a lookup with each verification started and return info about the phone number. |
| `psd_2_enabled` | `TrueClass \| FalseClass` | Optional | Whether to pass PSD2 transaction parameters when starting a verification. |
| `skip_sms_to_landlines` | `TrueClass \| FalseClass` | Optional | Whether to skip sending SMS verifications to landlines. Requires `lookup_enabled`. |
| `dtmf_input_required` | `TrueClass \| FalseClass` | Optional | Whether to ask the user to press a number before delivering the verify code in a phone call. |
| `tts_name` | `String` | Optional | The name of an alternative text-to-speech service to use in phone calls. Applies only to TTS languages. |
| `do_not_share_warning_enabled` | `TrueClass \| FalseClass` | Optional | Whether to add a security warning at the end of an SMS verification body. Disabled by default and applies only to SMS. Example SMS body: `Your AppName verification code is: 1234. Don’t share this code with anyone; our employees will never ask for the code` |
| `custom_code_enabled` | `TrueClass \| FalseClass` | Optional | Whether to allow sending verifications with a custom code instead of a randomly generated one. |
| `push` | `Object` | Optional | Configurations for the Push factors (channel) created under this Service. |
| `totp` | `Object` | Optional | Configurations for the TOTP factors (channel) created under this Service. |
| `default_template_sid` | `String` | Optional | **Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HJ[0-9a-fA-F]{32}$` |
| `whatsapp` | `Object` | Optional | - |
| `passkeys` | `Object` | Optional | - |
| `verify_event_subscription_enabled` | `TrueClass \| FalseClass` | Optional | Whether to allow verifications from the service to reach the stream-events sinks if configured |
| `date_created` | `DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `date_updated` | `DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. |
| `url` | `String` | Optional | The absolute URL of the resource. |
| `links` | `Object` | Optional | The URLs of related resources. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "code_length": 0,
  "sid": "sid6",
  "account_sid": "account_sid0",
  "friendly_name": "friendly_name0",
  "lookup_enabled": false,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

