
# Getting Started with Twilio APIs

## Install the Package

Install the gem from the command line:

```bash
gem install twilio-api-sdk -v 1.0.0
```

Or add the gem to your Gemfile and run `bundle`:

```ruby
gem 'twilio-api-sdk', '1.0.0'
```

For additional gem details, see the [RubyGems page for the twilio-api-sdk gem](https://rubygems.org/gems/twilio-api-sdk/versions/1.0.0).

## IRB Console Usage

You can explore the SDK interactively using IRB in two ways

### 1. Use IRB with Installed Gem

Open your system terminal (Command Prompt, Git Bash or macOS Terminal) and type the following command to start the irb console.

```bash
irb
```

Now you can load the SDK in the IRB

```ruby
require 'twilio_ap_is'
include TwilioApIs
```

### 2. Use IRB within SDK

Open your system terminal (Command Prompt, Git Bash or macOS Terminal) and navigate to the root folder of SDK.

```
cd path/to/twilio_ap_is
```

Now you can start the preconfigured irb console by running the following command

```bash
ruby bin/console
```

**_Note:_** This automatically loads the SDK from lib/

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| connection | `Faraday::Connection` | The Faraday connection object passed by the SDK user for making requests |
| adapter | `Faraday::Adapter` | The Faraday adapter object passed by the SDK user for performing http requests |
| timeout | `Float` | The value to use for connection timeout. <br> **Default: 30** |
| max_retries | `Integer` | The number of times to retry an endpoint call if it fails. <br> **Default: 0** |
| retry_interval | `Float` | Pause in seconds between retries. <br> **Default: 1** |
| backoff_factor | `Float` | The amount to multiply each successive retry's interval amount by in order to provide backoff. <br> **Default: 2** |
| retry_statuses | `Array` | A list of HTTP statuses to retry. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| retry_methods | `Array` | A list of HTTP methods to retry. <br> **Default: %i[get put]** |
| http_callback | `HttpCallBack` | The Http CallBack allows defining callables for pre and post API calls. |
| proxy_settings | [`ProxySettings`](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/proxy-settings.md) | Optional proxy configuration to route HTTP requests through a proxy server. |
| logging_configuration | [`LoggingConfiguration`](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/logging-configuration.md) | The SDK logging configuration for API calls |
| basic_auth_credentials | [`BasicAuthCredentials`](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/auth/basic-authentication.md) | The credential object for Basic Authentication |

The API client can be initialized as follows:

### Code-Based Client Initialization

```ruby
require 'twilio_ap_is'
include TwilioApIs

client = Client.new(
  basic_auth_credentials: BasicAuthCredentials.new(
    username: 'BasicAuthUserName',
    password: 'BasicAuthPassword'
  ),
  environment: Environment::PRODUCTION,
  logging_configuration: LoggingConfiguration.new(
    log_level: Logger::INFO,
    request_logging_config: RequestLoggingConfiguration.new(
      log_body: true
    ),
    response_logging_config: ResponseLoggingConfiguration.new(
      log_headers: true
    )
  )
)
```

### Environment-Based Client Initialization

```ruby
require 'twilio_ap_is'
include TwilioApIs

# Create client from environment
client = Client.from_env
```

See the [`Environment-Based Client Initialization`](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/environment-based-client-initialization.md) section for details.

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| PRODUCTION | **Default** |

## Authorization

This API uses the following authentication schemes.

* [`accountSid_authToken (Basic Authentication)`](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/auth/basic-authentication.md)

## List of APIs

* [Accounts V1 Auth Token Promotion](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-auth-token-promotion.md)
* [Accounts V1 Aws](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-aws.md)
* [Accounts V1 Bulk Consents](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-bulk-consents.md)
* [Accounts V1 Bulk Contacts](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-bulk-contacts.md)
* [Accounts V1 Messaging Geopermissions](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-messaging-geopermissions.md)
* [Accounts V1 Public Key](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-public-key.md)
* [Accounts V1 Safelist](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-safelist.md)
* [Accounts V1 Secondary Auth Token](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/accounts-v1-secondary-auth-token.md)
* [Chat V3 Channel](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/chat-v3-channel.md)
* [Conversations V1 Address Configuration](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-address-configuration.md)
* [Conversations V1 Binding](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-binding.md)
* [Conversations V1 Configuration](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-configuration.md)
* [Conversations V1 Conversation](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-conversation.md)
* [Conversations V1 Conversation with Participants](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-conversation-with-participants.md)
* [Conversations V1 Credential](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-credential.md)
* [Conversations V1 Delivery Receipt](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-delivery-receipt.md)
* [Conversations V1 Message](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-message.md)
* [Conversations V1 Notification](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-notification.md)
* [Conversations V1 Participant](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-participant.md)
* [Conversations V1 Participant Conversation](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-participant-conversation.md)
* [Conversations V1 Role](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-role.md)
* [Conversations V1 Service](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-service.md)
* [Conversations V1 User](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-user.md)
* [Conversations V1 User Conversation](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-user-conversation.md)
* [Conversations V1 Webhook](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/conversations-v1-webhook.md)
* [Notify V1 Binding](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/notify-v1-binding.md)
* [Notify V1 Credential](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/notify-v1-credential.md)
* [Notify V1 Notification](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/notify-v1-notification.md)
* [Notify V1 Service](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/notify-v1-service.md)
* [Taskrouter V1 Activity](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-activity.md)
* [Taskrouter V1 Event](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-event.md)
* [Taskrouter V1 Task](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task.md)
* [Taskrouter V1 Task Channel](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-channel.md)
* [Taskrouter V1 Task Queue](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-queue.md)
* [Taskrouter V1 Task Queue Bulk Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-queue-bulk-real-time-statistics.md)
* [Taskrouter V1 Task Queue Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-queue-cumulative-statistics.md)
* [Taskrouter V1 Task Queue Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-queue-real-time-statistics.md)
* [Taskrouter V1 Task Queue Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-queue-statistics.md)
* [Taskrouter V1 Task Queues Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-queues-statistics.md)
* [Taskrouter V1 Task Reservation](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-task-reservation.md)
* [Taskrouter V1 Worker](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-worker.md)
* [Taskrouter V1 Worker Channel](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-worker-channel.md)
* [Taskrouter V1 Worker Reservation](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-worker-reservation.md)
* [Taskrouter V1 Worker Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-worker-statistics.md)
* [Taskrouter V1 Workers Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workers-cumulative-statistics.md)
* [Taskrouter V1 Workers Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workers-real-time-statistics.md)
* [Taskrouter V1 Workers Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workers-statistics.md)
* [Taskrouter V1 Workflow](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workflow.md)
* [Taskrouter V1 Workflow Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workflow-cumulative-statistics.md)
* [Taskrouter V1 Workflow Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workflow-real-time-statistics.md)
* [Taskrouter V1 Workflow Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workflow-statistics.md)
* [Taskrouter V1 Workspace](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workspace.md)
* [Taskrouter V1 Workspace Cumulative Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workspace-cumulative-statistics.md)
* [Taskrouter V1 Workspace Real Time Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workspace-real-time-statistics.md)
* [Taskrouter V1 Workspace Statistics](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/taskrouter-v1-workspace-statistics.md)
* [Verify V2 Service](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/verify-v2-service.md)
* [Verify V2 Verification](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/verify-v2-verification.md)
* [Verify V2 Verification Check](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/controllers/verify-v2-verification-check.md)

## SDK Infrastructure

### Configuration

* [ProxySettings](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/proxy-settings.md)
* [Environment-Based Client Initialization](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/environment-based-client-initialization.md)
* [AbstractLogger](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/abstract-logger.md)
* [LoggingConfiguration](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/logging-configuration.md)
* [RequestLoggingConfiguration](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/request-logging-configuration.md)
* [ResponseLoggingConfiguration](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/response-logging-configuration.md)

### HTTP

* [HttpResponse](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/http-response.md)
* [HttpRequest](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/http-request.md)

### Utilities

* [ApiResponse](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/api-response.md)
* [ApiHelper](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/api-helper.md)
* [DateTimeHelper](https://www.github.com/sdks-io/twilio-api-sdk-ruby/tree/1.0.0/doc/date-time-helper.md)

