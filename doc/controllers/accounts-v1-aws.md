# Accounts V1 Aws

```ruby
accounts_v1_aws_api = client.accounts_v1_aws
```

## Class Name

`AccountsV1AwsApi`

## Methods

* [List Credential Aws](../../doc/controllers/accounts-v1-aws.md#list-credential-aws)
* [Create Credential Aws](../../doc/controllers/accounts-v1-aws.md#create-credential-aws)
* [Fetch Credential Aws](../../doc/controllers/accounts-v1-aws.md#fetch-credential-aws)
* [Update Credential Aws](../../doc/controllers/accounts-v1-aws.md#update-credential-aws)
* [Delete Credential Aws](../../doc/controllers/accounts-v1-aws.md#delete-credential-aws)


# List Credential Aws

Retrieves a collection of AWS Credentials belonging to the account used to make the request

```ruby
def list_credential_aws(page_size: nil,
                        page: nil,
                        page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListCredentialAwsResponse`](../../doc/models/list-credential-aws-response.md).

## Example Usage

```ruby
result = accounts_v1_aws_api.list_credential_aws

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "credentials": [],
  "meta": {
    "first_page_url": "https://accounts.twilio.com/v1/Credentials/AWS?PageSize=50&Page=0",
    "key": "credentials",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://accounts.twilio.com/v1/Credentials/AWS?PageSize=50&Page=0"
  }
}
```


# Create Credential Aws

Create a new AWS Credential

```ruby
def create_credential_aws(credentials,
                          friendly_name: nil,
                          account_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `credentials` | `String` | Form, Required | A string that contains the AWS access credentials in the format `<AWS_ACCESS_KEY_ID>:<AWS_SECRET_ACCESS_KEY>`. For example, `AKIAIOSFODNN7EXAMPLE:wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY` |
| `friendly_name` | `String` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `account_sid` | `String` | Form, Optional | The SID of the Subaccount that this Credential should be associated with. Must be a valid Subaccount of the account issuing the request.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`CredentialAws`](../../doc/models/credential-aws.md).

## Example Usage

```ruby
credentials = 'aws_credentials'

friendly_name = 'friendly_name'

account_sid = 'ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = accounts_v1_aws_api.create_credential_aws(
  credentials,
  friendly_name: friendly_name,
  account_sid: account_sid
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
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Fetch Credential Aws

Fetch the AWS credentials specified by the provided Credential Sid

```ruby
def fetch_credential_aws(sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`CredentialAws`](../../doc/models/credential-aws.md).

## Example Usage

```ruby
sid = 'Sid8'

result = accounts_v1_aws_api.fetch_credential_aws(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Credential Aws

Modify the properties of a given Account

```ruby
def update_credential_aws(sid,
                          friendly_name: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`CredentialAws`](../../doc/models/credential-aws.md).

## Example Usage

```ruby
sid = 'Sid8'

friendly_name = 'friendly_name'

result = accounts_v1_aws_api.update_credential_aws(
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
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential Aws

Delete a Credential from your account

```ruby
def delete_credential_aws(sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
sid = 'Sid8'

result = accounts_v1_aws_api.delete_credential_aws(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

