
# Safelist

*This model accepts additional fields of type Object.*

## Structure

`Safelist`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Optional | The unique string that we created to identify the SafeList resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^GN[0-9a-fA-F]{32}$` |
| `phone_number` | `String` | Optional | The phone number or phone number 1k prefix in SafeList. |
| `additional_properties` | `Hash[String, Object]` | Optional | - |

## Example (as JSON)

```json
{
  "sid": "sid2",
  "phone_number": "phone_number6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

