---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "checkly_trigger_check Resource - terraform-provider-checkly"
subcategory: ""
description: |-
  
---

# checkly_trigger_check (Resource)



## Example Usage

```terraform
resource "checkly_trigger_check" "test_trigger_check" {
  check_id = "c1ff95c5-d7f6-4a90-9ce2-1e605f117592"
}

output "test_trigger_check_url" {
  value = checkly_trigger_check.test_trigger_check.url
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `check_id` (String) The id of the check that you want to attach the trigger to.

### Optional

- `id` (String) The ID of this resource.
- `token` (String) The token value created to trigger the check
- `url` (String) The request URL to trigger the check run.


