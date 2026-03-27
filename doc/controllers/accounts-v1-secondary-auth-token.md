# Accounts V1 Secondary Auth Token

```ruby
accounts_v1_secondary_auth_token_api = client.accounts_v1_secondary_auth_token
```

## Class Name

`AccountsV1SecondaryAuthTokenApi`

## Methods

* [Create Secondary Auth Token](../../doc/controllers/accounts-v1-secondary-auth-token.md#create-secondary-auth-token)
* [Delete Secondary Auth Token](../../doc/controllers/accounts-v1-secondary-auth-token.md#delete-secondary-auth-token)


# Create Secondary Auth Token

Create a new secondary Auth Token

```ruby
def create_secondary_auth_token
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`SecondaryAuthToken`](../../doc/models/secondary-auth-token.md).

## Example Usage

```ruby
result = accounts_v1_secondary_auth_token_api.create_secondary_auth_token

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
  "secondary_auth_token": "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb",
  "url": "https://accounts.twilio.com/v1/AuthTokens/Secondary"
}
```


# Delete Secondary Auth Token

Delete the secondary Auth Token from your account

```ruby
def delete_secondary_auth_token
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
result = accounts_v1_secondary_auth_token_api.delete_secondary_auth_token

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

