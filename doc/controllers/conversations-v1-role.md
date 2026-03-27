# Conversations V1 Role

```ruby
conversations_v1_role_api = client.conversations_v1_role
```

## Class Name

`ConversationsV1RoleApi`

## Methods

* [Create Role](../../doc/controllers/conversations-v1-role.md#create-role)
* [List Role](../../doc/controllers/conversations-v1-role.md#list-role)
* [Update Role](../../doc/controllers/conversations-v1-role.md#update-role)
* [Delete Role](../../doc/controllers/conversations-v1-role.md#delete-role)
* [Fetch Role](../../doc/controllers/conversations-v1-role.md#fetch-role)
* [Create Service Role](../../doc/controllers/conversations-v1-role.md#create-service-role)
* [List Service Role](../../doc/controllers/conversations-v1-role.md#list-service-role)
* [Update Service Role](../../doc/controllers/conversations-v1-role.md#update-service-role)
* [Delete Service Role](../../doc/controllers/conversations-v1-role.md#delete-service-role)
* [Fetch Service Role](../../doc/controllers/conversations-v1-role.md#fetch-service-role)


# Create Role

Create a new user role in your account's default service

```ruby
def create_role(friendly_name,
                type,
                permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendly_name` | `String` | Form, Required | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `type` | [`RoleRoleType`](../../doc/models/role-role-type.md) | Form, Required | The type of role. Can be: `conversation` for [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) roles or `service` for [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) roles. |
| `permission` | `Array[String]` | Form, Required | A permission that you grant to the new role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. The values for this parameter depend on the role's `type`. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Role`](../../doc/models/role.md).

## Example Usage

```ruby
friendly_name = 'Conversation Role'

type = RoleRoleType::CONVERSATION

permission = [
  'Permission5'
]

result = conversations_v1_role_api.create_role(
  friendly_name,
  type,
  permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Role

Retrieve a list of all user roles in your account's default service

```ruby
def list_role(page_size: nil,
              page: nil,
              page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListRoleResponse`](../../doc/models/list-role-response.md).

## Example Usage

```ruby
result = conversations_v1_role_api.list_role

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Roles?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Roles?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "roles"
  },
  "roles": [
    {
      "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Conversation Role",
      "type": "conversation",
      "permissions": [
        "sendMessage",
        "leaveConversation",
        "editOwnMessage",
        "deleteOwnMessage"
      ],
      "date_created": "2016-03-03T19:47:15Z",
      "date_updated": "2016-03-03T19:47:15Z",
      "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Update Role

Update an existing user role in your account's default service

```ruby
def update_role(sid,
                permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | The SID of the Role resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `permission` | `Array[String]` | Form, Required | A permission that you grant to the role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. Note that the update action replaces all previously assigned permissions with those defined in the update action. To remove a permission, do not include it in the subsequent update action. The values for this parameter depend on the role's `type`. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Role`](../../doc/models/role.md).

## Example Usage

```ruby
sid = 'Sid8'

permission = [
  'Permission5'
]

result = conversations_v1_role_api.update_role(
  sid,
  permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Role

Remove a user role from your account's default service

```ruby
def delete_role(sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | The SID of the Role resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
sid = 'Sid8'

result = conversations_v1_role_api.delete_role(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Role

Fetch a user role from your account's default service

```ruby
def fetch_role(sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `String` | Template, Required | The SID of the Role resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`Role`](../../doc/models/role.md).

## Example Usage

```ruby
sid = 'Sid8'

result = conversations_v1_role_api.fetch_role(sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Create Service Role

Create a new user role in your service

```ruby
def create_service_role(chat_service_sid,
                        friendly_name,
                        type,
                        permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to create the Role resource under.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `friendly_name` | `String` | Form, Required | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `type` | [`ServiceRoleRoleType`](../../doc/models/service-role-role-type.md) | Form, Required | The type of role. Can be: `conversation` for [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) roles or `service` for [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) roles. |
| `permission` | `Array[String]` | Form, Required | A permission that you grant to the new role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. The values for this parameter depend on the role's `type`. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceRole`](../../doc/models/service-role.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

friendly_name = 'Conversation Role'

type = ServiceRoleRoleType::CONVERSATION

permission = [
  'Permission5'
]

result = conversations_v1_role_api.create_service_role(
  chat_service_sid,
  friendly_name,
  type,
  permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Service Role

Retrieve a list of all user roles in your service

```ruby
def list_service_role(chat_service_sid,
                      page_size: nil,
                      page: nil,
                      page_token: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to read the Role resources from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `page_size` | `Integer` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `Integer` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `page_token` | `String` | Query, Optional | The page token. This is provided by the API. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ListServiceRoleResponse`](../../doc/models/list-service-role-response.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

result = conversations_v1_role_api.list_service_role(chat_service_sid)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "roles"
  },
  "roles": [
    {
      "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Conversation Role",
      "type": "conversation",
      "permissions": [
        "sendMessage",
        "leaveConversation",
        "editOwnMessage",
        "deleteOwnMessage"
      ],
      "date_created": "2016-03-03T19:47:15Z",
      "date_updated": "2016-03-03T19:47:15Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Update Service Role

Update an existing user role in your service

```ruby
def update_service_role(chat_service_sid,
                        sid,
                        permission)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to update the Role resource in.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Role resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `permission` | `Array[String]` | Form, Required | A permission that you grant to the role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. Note that the update action replaces all previously assigned permissions with those defined in the update action. To remove a permission, do not include it in the subsequent update action. The values for this parameter depend on the role's `type`. |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceRole`](../../doc/models/service-role.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

sid = 'Sid8'

permission = [
  'Permission5'
]

result = conversations_v1_role_api.update_service_role(
  chat_service_sid,
  sid,
  permission
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Service Role

Remove a user role from your service

```ruby
def delete_service_role(chat_service_sid,
                        sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to delete the Role resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Role resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

sid = 'Sid8'

result = conversations_v1_role_api.delete_service_role(
  chat_service_sid,
  sid
)

if result.success?
  puts result.data
elsif result.error?
  warn result.errors
end
```


# Fetch Service Role

Fetch a user role from your service

```ruby
def fetch_service_role(chat_service_sid,
                       sid)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chat_service_sid` | `String` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to fetch the Role resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `String` | Template, Required | The SID of the Role resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT2`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ServiceRole`](../../doc/models/service-role.md).

## Example Usage

```ruby
chat_service_sid = 'ChatServiceSid4'

sid = 'Sid8'

result = conversations_v1_role_api.fetch_service_role(
  chat_service_sid,
  sid
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
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

