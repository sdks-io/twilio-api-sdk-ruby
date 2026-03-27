
# Verification Template

*This model accepts additional fields of type Object.*

## Structure

`VerificationTemplate`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | A 34 character string that uniquely identifies a Verification Template.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HJ[0-9a-fA-F]{32}$` |
| `account_sid` | `String` | Optional | The unique SID identifier of the Account.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Optional | A descriptive string that you create to describe a Template. It can be up to 32 characters long. |
| `channels` | `Array[String]` | Optional | A list of channels that support the Template. Can include: sms, voice. |
| `translations` | `Object` | Optional | An object that contains the different translations of the template. Every translation is identified by the language short name and contains its respective information as the approval status, text and created/modified date. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid8",
  "account_sid": "account_sid2",
  "friendly_name": "friendly_name2",
  "channels": [
    "channels1",
    "channels0"
  ],
  "translations": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

