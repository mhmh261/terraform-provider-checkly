---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "checkly_alert_channel Resource - terraform-provider-checkly"
subcategory: ""
description: |-
  Allows you to define alerting channels for the checks and groups in your account
---

# checkly_alert_channel (Resource)

Allows you to define alerting channels for the checks and groups in your account

## Example Usage

```terraform
# An Email alert channel
resource "checkly_alert_channel" "email_ac" {
  email {
    address = "john@example.com"
  }
  send_recovery = true
  send_failure = false
  send_degraded = true
  ssl_expiry = true
  ssl_expiry_threshold = 22
}

# A SMS alert channel
resource "checkly_alert_channel" "sms_ac" {
  sms {
    name = "john"
    number = "+5491100001111"
  }
  send_recovery = true
  send_failure = true
}

# A Slack alert channel
resource "checkly_alert_channel" "slack_ac" {
  slack {
    channel = "#checkly-notifications"
    url = "https://slack.com/webhook"
  }
}

# An Opsgenie alert channel
resource "checkly_alert_channel" "opsgenie_ac" {
  opsgenie {
    name = "opsalerts"
    api_key = "fookey"
    region = "fooregion"
    priority = "foopriority"
  }
}

# An Pagerduty alert channel
resource "checkly_alert_channel" "pagerduty_ac" {
  pagerduty {
    account      = "checkly"
    service_key  = "key1"
    service_name = "pdalert"
  }
}

# An Webhook alert channel
resource "checkly_alert_channel" "webhook_ac" {
  webhook {
    name = "foo"
    method = "get"
    template = "footemplate"
    url = "https://example.com/foo"
    webhook_secret = "foosecret"
  }
}

# Connecting the alert channel to a check
resource "checkly_check" "example-check" {
  name = "Example check"

  alert_channel_subscription {
    channel_id = checkly_alert_channel.email_ac.id
    activated  = true
  }

  alert_channel_subscription {
    channel_id = checkly_alert_channel.sms_ac.id
    activated  = true
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- `email` (Block Set, Max: 1) (see [below for nested schema](#nestedblock--email))
- `id` (String) The ID of this resource.
- `opsgenie` (Block Set, Max: 1) (see [below for nested schema](#nestedblock--opsgenie))
- `pagerduty` (Block Set, Max: 1) (see [below for nested schema](#nestedblock--pagerduty))
- `send_degraded` (Boolean) (Default `false`)
- `send_failure` (Boolean) (Default `true`)
- `send_recovery` (Boolean) (Default `true`)
- `slack` (Block Set, Max: 1) (see [below for nested schema](#nestedblock--slack))
- `sms` (Block Set, Max: 1) (see [below for nested schema](#nestedblock--sms))
- `ssl_expiry` (Boolean) (Default `false`)
- `ssl_expiry_threshold` (Number) Value must be between 1 and 30 (Default `30`)
- `webhook` (Block Set, Max: 1) (see [below for nested schema](#nestedblock--webhook))

<a id="nestedblock--email"></a>
### Nested Schema for `email`

Required:

- `address` (String) The email address of this email alert channel.


<a id="nestedblock--opsgenie"></a>
### Nested Schema for `opsgenie`

Required:

- `api_key` (String)
- `name` (String)
- `priority` (String)
- `region` (String)


<a id="nestedblock--pagerduty"></a>
### Nested Schema for `pagerduty`

Required:

- `service_key` (String)

Optional:

- `account` (String)
- `service_name` (String)


<a id="nestedblock--slack"></a>
### Nested Schema for `slack`

Required:

- `channel` (String) The name of the alert's Slack channel
- `url` (String) The Slack webhook URL


<a id="nestedblock--sms"></a>
### Nested Schema for `sms`

Required:

- `name` (String) The name of this alert channel
- `number` (String) The mobile number to receive the alerts


<a id="nestedblock--webhook"></a>
### Nested Schema for `webhook`

Required:

- `name` (String)
- `url` (String)

Optional:

- `headers` (Map of String)
- `method` (String) (Default `POST`)
- `query_parameters` (Map of String)
- `template` (String)
- `webhook_secret` (String)

