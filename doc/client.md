
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| connection | `Faraday::Connection` | The Faraday connection object passed by the SDK user for making requests |
| adapter | `Faraday::Adapter` | The Faraday adapter object passed by the SDK user for performing http requests |
| timeout | `Float` | The value to use for connection timeout. <br> **Default: 30** |
| max_retries | `Integer` | The number of times to retry an endpoint call if it fails. <br> **Default: 0** |
| retry_interval | `Float` | Pause in seconds between retries. <br> **Default: 1** |
| backoff_factor | `Float` | The amount to multiply each successive retry's interval amount by in order to provide backoff. <br> **Default: 2** |
| retry_statuses | `Array` | A list of HTTP statuses to retry. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| retry_methods | `Array` | A list of HTTP methods to retry. <br> **Default: %i[get put]** |
| http_callback | `HttpCallBack` | The Http CallBack allows defining callables for pre and post API calls. |
| proxy_settings | [`ProxySettings`](../doc/proxy-settings.md) | Optional proxy configuration to route HTTP requests through a proxy server. |
| logging_configuration | [`LoggingConfiguration`](../doc/logging-configuration.md) | The SDK logging configuration for API calls |
| basic_auth_credentials | [`BasicAuthCredentials`](auth/basic-authentication.md) | The credential object for Basic Authentication |

The API client can be initialized as follows:

## Code-Based Client Initialization

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

## Environment-Based Client Initialization

```ruby
require 'twilio_ap_is'
include TwilioApIs

# Create client from environment
client = Client.from_env
```

See the [`Environment-Based Client Initialization`](../doc/environment-based-client-initialization.md) section for details.

## Twilio APIs Client

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

## Apis

| Name | Description |
|  --- | --- |
| accounts_v_1_auth_token_promotion | Gets AccountsV1AuthTokenPromotionApi |
| accounts_v_1_aws | Gets AccountsV1AwsApi |
| accounts_v_1_bulk_consents | Gets AccountsV1BulkConsentsApi |
| accounts_v_1_bulk_contacts | Gets AccountsV1BulkContactsApi |
| accounts_v_1_messaging_geopermissions | Gets AccountsV1MessagingGeopermissionsApi |
| accounts_v_1_public_key | Gets AccountsV1PublicKeyApi |
| accounts_v_1_safelist | Gets AccountsV1SafelistApi |
| accounts_v_1_secondary_auth_token | Gets AccountsV1SecondaryAuthTokenApi |
| chat_v_3_channel | Gets ChatV3ChannelApi |
| conversations_v_1_address_configuration | Gets ConversationsV1AddressConfigurationApi |
| conversations_v_1_binding | Gets ConversationsV1BindingApi |
| conversations_v_1_configuration | Gets ConversationsV1ConfigurationApi |
| conversations_v_1_conversation | Gets ConversationsV1ConversationApi |
| conversations_v_1_conversation_with_participants | Gets ConversationsV1ConversationWithParticipantsApi |
| conversations_v_1_credential | Gets ConversationsV1CredentialApi |
| conversations_v_1_delivery_receipt | Gets ConversationsV1DeliveryReceiptApi |
| conversations_v_1_message | Gets ConversationsV1MessageApi |
| conversations_v_1_notification | Gets ConversationsV1NotificationApi |
| conversations_v_1_participant | Gets ConversationsV1ParticipantApi |
| conversations_v_1_participant_conversation | Gets ConversationsV1ParticipantConversationApi |
| conversations_v_1_role | Gets ConversationsV1RoleApi |
| conversations_v_1_service | Gets ConversationsV1ServiceApi |
| conversations_v_1_user | Gets ConversationsV1UserApi |
| conversations_v_1_user_conversation | Gets ConversationsV1UserConversationApi |
| conversations_v_1_webhook | Gets ConversationsV1WebhookApi |
| notify_v_1_binding | Gets NotifyV1BindingApi |
| notify_v_1_credential | Gets NotifyV1CredentialApi |
| notify_v_1_notification | Gets NotifyV1NotificationApi |
| notify_v_1_service | Gets NotifyV1ServiceApi |
| taskrouter_v_1_activity | Gets TaskrouterV1ActivityApi |
| taskrouter_v_1_event | Gets TaskrouterV1EventApi |
| taskrouter_v_1_task | Gets TaskrouterV1TaskApi |
| taskrouter_v_1_task_channel | Gets TaskrouterV1TaskChannelApi |
| taskrouter_v_1_task_queue | Gets TaskrouterV1TaskQueueApi |
| taskrouter_v_1_task_queue_bulk_real_time_statistics | Gets TaskrouterV1TaskQueueBulkRealTimeStatisticsApi |
| taskrouter_v_1_task_queue_cumulative_statistics | Gets TaskrouterV1TaskQueueCumulativeStatisticsApi |
| taskrouter_v_1_task_queue_real_time_statistics | Gets TaskrouterV1TaskQueueRealTimeStatisticsApi |
| taskrouter_v_1_task_queue_statistics | Gets TaskrouterV1TaskQueueStatisticsApi |
| taskrouter_v_1_task_queues_statistics | Gets TaskrouterV1TaskQueuesStatisticsApi |
| taskrouter_v_1_task_reservation | Gets TaskrouterV1TaskReservationApi |
| taskrouter_v_1_worker | Gets TaskrouterV1WorkerApi |
| taskrouter_v_1_worker_channel | Gets TaskrouterV1WorkerChannelApi |
| taskrouter_v_1_worker_reservation | Gets TaskrouterV1WorkerReservationApi |
| taskrouter_v_1_worker_statistics | Gets TaskrouterV1WorkerStatisticsApi |
| taskrouter_v_1_workers_cumulative_statistics | Gets TaskrouterV1WorkersCumulativeStatisticsApi |
| taskrouter_v_1_workers_real_time_statistics | Gets TaskrouterV1WorkersRealTimeStatisticsApi |
| taskrouter_v_1_workers_statistics | Gets TaskrouterV1WorkersStatisticsApi |
| taskrouter_v_1_workflow | Gets TaskrouterV1WorkflowApi |
| taskrouter_v_1_workflow_cumulative_statistics | Gets TaskrouterV1WorkflowCumulativeStatisticsApi |
| taskrouter_v_1_workflow_real_time_statistics | Gets TaskrouterV1WorkflowRealTimeStatisticsApi |
| taskrouter_v_1_workflow_statistics | Gets TaskrouterV1WorkflowStatisticsApi |
| taskrouter_v_1_workspace | Gets TaskrouterV1WorkspaceApi |
| taskrouter_v_1_workspace_cumulative_statistics | Gets TaskrouterV1WorkspaceCumulativeStatisticsApi |
| taskrouter_v_1_workspace_real_time_statistics | Gets TaskrouterV1WorkspaceRealTimeStatisticsApi |
| taskrouter_v_1_workspace_statistics | Gets TaskrouterV1WorkspaceStatisticsApi |
| verify_v_2_service | Gets VerifyV2ServiceApi |
| verify_v_2_verification | Gets VerifyV2VerificationApi |
| verify_v_2_verification_check | Gets VerifyV2VerificationCheckApi |
| sms | Gets SmsApi |

