---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "rhoas_topic Resource - terraform-provider-rhoas"
subcategory: ""
description: |-
  rhoas_topic manages a topic in a  Kafka instance in Red Hat OpenShift Streams for Apache Kafka.
---

# rhoas_topic (Resource)

`rhoas_topic` manages a topic in a  Kafka instance in Red Hat OpenShift Streams for Apache Kafka.

## Example Usage

```terraform
terraform {
  required_providers {
    rhoas = {
      source  = "registry.terraform.io/redhat-developer/rhoas"
      version = "0.1"
    }
  }
}

provider "rhoas" {}

resource "rhoas_kafka" "foo" {
  name = "foo"
}

resource "rhoas_topic" "bar" {
  name       = "bar-post"
  partitions = 4
  kafka_id   = rhoas_kafka.foo.id

  depends_on = [
    rhoas_kafka.foo
  ]
}

output "topic_bar" {
  value = rhoas_topic.bar
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `kafka_id` (String) The unique ID of the kafka instance this topic is associated with
- `name` (String) The name of the topic
- `partitions` (Number) The number of partitions in the topic

### Optional

- `timeouts` (Block, Optional) (see [below for nested schema](#nestedblock--timeouts))

### Read-Only

- `id` (String) The ID of this resource.

<a id="nestedblock--timeouts"></a>
### Nested Schema for `timeouts`

Optional:

- `create` (String)


