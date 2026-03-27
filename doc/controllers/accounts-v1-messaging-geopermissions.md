# Accounts V1 Messaging Geopermissions

```ruby
accounts_v1_messaging_geopermissions_api = client.accounts_v1_messaging_geopermissions
```

## Class Name

`AccountsV1MessagingGeopermissionsApi`

## Methods

* [Update Messaging Geopermissions](../../doc/controllers/accounts-v1-messaging-geopermissions.md#update-messaging-geopermissions)
* [Fetch Messaging Geopermissions](../../doc/controllers/accounts-v1-messaging-geopermissions.md#fetch-messaging-geopermissions)


# Update Messaging Geopermissions

Manage Geo Permissions for each country.

```ruby
def update_messaging_geopermissions(permissions)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `permissions` | `Array[Object]` | Form, Required | A list of objects where each object represents the Geo Permission to be updated. Each object contains the following fields: `country_code`, unique code for each country of Geo Permission; `type`, permission type of the Geo Permission i.e. country; `enabled`, configure true for enabling the Geo Permission, false for disabling the Geo Permission. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`MsgGeopermissions`](../../doc/models/msg-geopermissions.md).

## Example Usage

```ruby
permissions = [
  JSON.parse('"{\\"country_code\\": \\"IN\\",\\"type\\": \\"country\\", \\"enabled\\": false}"'),
  JSON.parse('"{\\"country_code\\": \\"PK\\",\\"type\\": \\"country\\", \\"enabled\\": true}"')
]

result = accounts_v1_messaging_geopermissions_api.update_messaging_geopermissions(permissions)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Messaging Geopermissions

Manage Geo Permissions for each country.

```ruby
def fetch_messaging_geopermissions(country_code: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `country_code` | `String` | Query, Optional | The country code to filter the geo permissions. If provided, only the geo permission for the specified country will be returned. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`MsgGeopermissions`](../../doc/models/msg-geopermissions.md).

## Example Usage

```ruby
country_code = 'IN,PK,US'

result = accounts_v1_messaging_geopermissions_api.fetch_messaging_geopermissions(country_code: country_code)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

