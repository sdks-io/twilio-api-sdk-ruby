# SMS

```ruby
sms_api = client.sms
```

## Class Name

`SmsApi`


# Create Message

Send a message

```ruby
def create_message(account_sid,
                   to,
                   status_callback: nil,
                   application_sid: nil,
                   max_price: nil,
                   provide_feedback: nil,
                   attempt: nil,
                   validity_period: nil,
                   force_delivery: nil,
                   content_retention: nil,
                   address_retention: nil,
                   smart_encoded: nil,
                   persistent_action: nil,
                   traffic_type: nil,
                   shorten_urls: nil,
                   schedule_type: nil,
                   send_at: nil,
                   send_as_mms: nil,
                   content_variables: nil,
                   risk_check: nil,
                   from: nil,
                   messaging_service_sid: nil,
                   body: nil,
                   media_url: nil,
                   content_sid: nil)
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `account_sid` | `String` | Template, Required | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) creating the Message resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |
| `to` | `String` | Form, Required | The recipient's phone number in [E.164](https://www.twilio.com/docs/glossary/what-e164) format (for SMS/MMS) or [channel address](https://www.twilio.com/docs/messaging/channels), e.g. `whatsapp:+15552229999`. |
| `status_callback` | `String` | Form, Optional | The URL of the endpoint to which Twilio sends [Message status callback requests](https://www.twilio.com/docs/sms/api/message-resource#twilios-request-to-the-statuscallback-url). URL must contain a valid hostname and underscores are not allowed. If you include this parameter with the `messaging_service_sid`, Twilio uses this URL instead of the Status Callback URL of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource). |
| `application_sid` | `String` | Form, Optional | The SID of the associated [TwiML Application](https://www.twilio.com/docs/usage/api/applications). [Message status callback requests](https://www.twilio.com/docs/sms/api/message-resource#twilios-request-to-the-statuscallback-url) are sent to the TwiML App's `message_status_callback` URL. Note that the `status_callback` parameter of a request takes priority over the `application_sid` parameter; if both are included `application_sid` is ignored.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AP[0-9a-fA-F]{32}$` |
| `max_price` | `Float` | Form, Optional | [OBSOLETE] This parameter will no longer have any effect as of 2024-06-03. |
| `provide_feedback` | `TrueClass \| FalseClass` | Form, Optional | Boolean indicating whether or not you intend to provide delivery confirmation feedback to Twilio (used in conjunction with the [Message Feedback subresource](https://www.twilio.com/docs/sms/api/message-feedback-resource)). Default value is `false`. |
| `attempt` | `Integer` | Form, Optional | Total number of attempts made (including this request) to send the message regardless of the provider used |
| `validity_period` | `Integer` | Form, Optional | The maximum length in seconds that the Message can remain in Twilio's outgoing message queue. If a queued Message exceeds the `validity_period`, the Message is not sent. Accepted values are integers from `1` to `36000`. Default value is `36000`. A `validity_period` greater than `5` is recommended. [Learn more about the validity period](https://www.twilio.com/blog/take-more-control-of-outbound-messages-using-validity-period-html) |
| `force_delivery` | `TrueClass \| FalseClass` | Form, Optional | Reserved |
| `content_retention` | [`MessageEnumContentRetention`](../../doc/models/message-enum-content-retention.md) | Form, Optional | Determines if the message content can be stored or redacted based on privacy settings |
| `address_retention` | [`MessageEnumAddressRetention`](../../doc/models/message-enum-address-retention.md) | Form, Optional | Determines if the address can be stored or obfuscated based on privacy settings |
| `smart_encoded` | `TrueClass \| FalseClass` | Form, Optional | Whether to detect Unicode characters that have a similar GSM-7 character and replace them. Can be: `true` or `false`. |
| `persistent_action` | `Array[String]` | Form, Optional | Rich actions for non-SMS/MMS channels. Used for [sending location in WhatsApp messages](https://www.twilio.com/docs/whatsapp/message-features#location-messages-with-whatsapp). |
| `traffic_type` | [`MessageEnumTrafficType`](../../doc/models/message-enum-traffic-type.md) | Form, Optional | - |
| `shorten_urls` | `TrueClass \| FalseClass` | Form, Optional | For Messaging Services with [Link Shortening configured](https://www.twilio.com/docs/messaging/features/link-shortening) only: A Boolean indicating whether or not Twilio should shorten links in the `body` of the Message. Default value is `false`. If `true`, the `messaging_service_sid` parameter must also be provided. |
| `schedule_type` | [`MessageEnumScheduleType`](../../doc/models/message-enum-schedule-type.md) | Form, Optional | For Messaging Services only: Include this parameter with a value of `fixed` in conjuction with the `send_time` parameter in order to [schedule a Message](https://www.twilio.com/docs/messaging/features/message-scheduling). |
| `send_at` | `DateTime` | Form, Optional | The time that Twilio will send the message. Must be in ISO 8601 format. |
| `send_as_mms` | `TrueClass \| FalseClass` | Form, Optional | If set to `true`, Twilio delivers the message as a single MMS message, regardless of the presence of media. |
| `content_variables` | `String` | Form, Optional | For [Content Editor/API](https://www.twilio.com/docs/content) only: Key-value pairs of [Template variables](https://www.twilio.com/docs/content/using-variables-with-content-api) and their substitution values. `content_sid` parameter must also be provided. If values are not defined in the `content_variables` parameter, the [Template's default placeholder values](https://www.twilio.com/docs/content/content-api-resources#create-templates) are used. |
| `risk_check` | [`VerificationEnumRiskCheck`](../../doc/models/verification-enum-risk-check.md) | Form, Optional | Include this parameter with a value of `disable` to skip any kind of risk check on the respective message request. |
| `from` | `String` | Form, Optional | The sender's Twilio phone number (in [E.164](https://en.wikipedia.org/wiki/E.164) format), [alphanumeric sender ID](https://www.twilio.com/docs/sms/quickstart), [Wireless SIM](https://www.twilio.com/docs/iot/wireless/programmable-wireless-send-machine-machine-sms-commands), [short code](https://www.twilio.com/en-us/messaging/channels/sms/short-codes), or [channel address](https://www.twilio.com/docs/messaging/channels) (e.g., `whatsapp:+15554449999`). The value of the `from` parameter must be a sender that is hosted within Twilio and belongs to the Account creating the Message. If you are using `messaging_service_sid`, this parameter can be empty (Twilio assigns a `from` value from the Messaging Service's Sender Pool) or you can provide a specific sender from your Sender Pool. |
| `messaging_service_sid` | `String` | Form, Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/messaging/services) you want to associate with the Message. When this parameter is provided and the `from` parameter is omitted, Twilio selects the optimal sender from the Messaging Service's Sender Pool. You may also provide a `from` parameter if you want to use a specific Sender from the Sender Pool.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `body` | `String` | Form, Optional | The text content of the outgoing message. Can be up to 1,600 characters in length. SMS only: If the `body` contains more than 160 [GSM-7](https://www.twilio.com/docs/glossary/what-is-gsm-7-character-encoding) characters (or 70 [UCS-2](https://www.twilio.com/docs/glossary/what-is-ucs-2-character-encoding) characters), the message is segmented and charged accordingly. For long `body` text, consider using the [send_as_mms parameter](https://www.twilio.com/blog/mms-for-long-text-messages). |
| `media_url` | `Array[String]` | Form, Optional | The URL of media to include in the Message content. `jpeg`, `jpg`, `gif`, and `png` file types are fully supported by Twilio and content is formatted for delivery on destination devices. The media size limit is 5 MB for supported file types (`jpeg`, `jpg`, `png`, `gif`) and 500 KB for [other types](https://www.twilio.com/docs/messaging/guides/accepted-mime-types) of accepted media. To send more than one image in the message, provide multiple `media_url` parameters in the POST request. You can include up to ten `media_url` parameters per message. [International](https://support.twilio.com/hc/en-us/articles/223179808-Sending-and-receiving-MMS-messages) and [carrier](https://support.twilio.com/hc/en-us/articles/223133707-Is-MMS-supported-for-all-carriers-in-US-and-Canada-) limits apply. |
| `content_sid` | `String` | Form, Optional | For [Content Editor/API](https://www.twilio.com/docs/content) only: The SID of the Content Template to be used with the Message, e.g., `HXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`. If this parameter is not provided, a Content Template is not used. Find the SID in the Console on the Content Editor page. For Content API users, the SID is found in Twilio's response when [creating the Template](https://www.twilio.com/docs/content/content-api-resources#create-templates) or by [fetching your Templates](https://www.twilio.com/docs/content/content-api-resources#fetch-all-content-resources).<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |

## Server

`Server::DEFAULT6`

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `data` property of this instance returns the response data which is of type [`ApiV2010AccountMessage`](../../doc/models/api-v2010-account-message.md).

## Example Usage

```ruby
account_sid = 'AccountSid0'

to = '+14155552345'

status_callback = 'https://example.com'

application_sid = 'APaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

persistent_action = [
  'mailto:test@example.com'
]

schedule_type = MessageEnumScheduleType::FIXED

from = '+14155552345'

messaging_service_sid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

body = 'Hello! 👍'

media_url = [
  'https://c1.staticflickr.com/3/2899/14341091933_1e92e62d12_b.jpg'
]

content_sid = 'HXaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa'

result = sms_api.create_message(
  account_sid,
  to,
  status_callback: status_callback,
  application_sid: application_sid,
  persistent_action: persistent_action,
  schedule_type: schedule_type,
  from: from,
  messaging_service_sid: messaging_service_sid,
  body: body,
  media_url: media_url,
  content_sid: content_sid
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
  "api_version": "2010-04-01",
  "body": "Hello! 👍",
  "date_created": "Thu, 24 Aug 2023 05:01:45 +0000",
  "date_sent": "Thu, 24 Aug 2023 05:01:45 +0000",
  "date_updated": "Thu, 24 Aug 2023 05:01:45 +0000",
  "direction": "outbound-api",
  "error_code": null,
  "error_message": null,
  "from": "+14155552345",
  "num_media": "0",
  "num_segments": "1",
  "price": null,
  "price_unit": null,
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "status": "queued",
  "subresource_uris": {
    "media": "/2010-04-01/Accounts/ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Media.json"
  },
  "to": "+14155552345",
  "uri": "/2010-04-01/Accounts/ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa.json"
}
```

