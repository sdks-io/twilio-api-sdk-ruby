# Conversations V1 Credential

```ruby
conversations_v1_credential_api = client.conversations_v1_credential
```

## Class Name

`ConversationsV1CredentialApi`

## Methods

* [Create Credential](../../doc/controllers/conversations-v1-credential.md#create-credential)
* [List Credential](../../doc/controllers/conversations-v1-credential.md#list-credential)
* [Update Credential](../../doc/controllers/conversations-v1-credential.md#update-credential)
* [Delete Credential](../../doc/controllers/conversations-v1-credential.md#delete-credential)
* [Fetch Credential](../../doc/controllers/conversations-v1-credential.md#fetch-credential)


# Create Credential

Add a new push notification credential to your account

```ruby
def create_credential(type,
                      friendly_name: nil,
                      certificate: nil,
                      private_key: nil,
                      sandbox: nil,
                      api_key: nil,
                      secret: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`CredentialPushType`](../../doc/models/credential-push-type.md) | Form, Required | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. |
| `friendly_name` | `String` | Form, Optional | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `certificate` | `String` | Form, Optional | [APN only] The URL encoded representation of the certificate. For example,<br>`-----BEGIN CERTIFICATE----- MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEF.....A== -----END CERTIFICATE-----`. |
| `private_key` | `String` | Form, Optional | [APN only] The URL encoded representation of the private key. For example,<br>`-----BEGIN RSA PRIVATE KEY----- MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fG... -----END RSA PRIVATE KEY-----`. |
| `sandbox` | `TrueClass \| FalseClass` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `api_key` | `String` | Form, Optional | [GCM only] The API key for the project that was obtained from the Google Developer console for your GCM Service application credential. |
| `secret` | `String` | Form, Optional | [FCM only] The **Server key** of your project from the Firebase console, found under Settings / Cloud messaging. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Credential`](../../doc/models/credential.md).

## Example Usage

```ruby
type = CredentialPushType::APN

result = conversations_v1_credential_api.create_credential(type)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Credential

Retrieve a list of all push notification credentials on your account

```ruby
def list_credential(page_size: nil,
                    page: nil,
                    page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListCredentialResponse`](../../doc/models/list-credential-response.md).

## Example Usage

```ruby
result = conversations_v1_credential_api.list_credential

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "credentials": [
    {
      "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Test slow create",
      "type": "apn",
      "sandbox": "False",
      "date_created": "2015-10-07T17:50:01Z",
      "date_updated": "2015-10-07T17:50:01Z",
      "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "credentials"
  }
}
```


# Update Credential

Update an existing push notification credential on your account

```ruby
def update_credential(sid,
                      type: nil,
                      friendly_name: nil,
                      certificate: nil,
                      private_key: nil,
                      sandbox: nil,
                      api_key: nil,
                      secret: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `type` | [`CredentialPushType`](../../doc/models/credential-push-type.md) | Form, Optional | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. |
| `friendly_name` | `String` | Form, Optional | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `certificate` | `String` | Form, Optional | [APN only] The URL encoded representation of the certificate. For example,<br>`-----BEGIN CERTIFICATE----- MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEF.....A== -----END CERTIFICATE-----`. |
| `private_key` | `String` | Form, Optional | [APN only] The URL encoded representation of the private key. For example,<br>`-----BEGIN RSA PRIVATE KEY----- MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fG... -----END RSA PRIVATE KEY-----`. |
| `sandbox` | `TrueClass \| FalseClass` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `api_key` | `String` | Form, Optional | [GCM only] The API key for the project that was obtained from the Google Developer console for your GCM Service application credential. |
| `secret` | `String` | Form, Optional | [FCM only] The **Server key** of your project from the Firebase console, found under Settings / Cloud messaging. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Credential`](../../doc/models/credential.md).

## Example Usage

```ruby
sid = 'Sid8'

friendly_name = 'Test slow create'

result = conversations_v1_credential_api.update_credential(
  sid,
  friendly_name: friendly_name
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential

Remove a push notification credential from your account

```ruby
def delete_credential(sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
sid = 'Sid8'

result = conversations_v1_credential_api.delete_credential(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Credential

Fetch a push notification credential from your account

```ruby
def fetch_credential(sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Credential`](../../doc/models/credential.md).

## Example Usage

```ruby
sid = 'Sid8'

result = conversations_v1_credential_api.fetch_credential(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

