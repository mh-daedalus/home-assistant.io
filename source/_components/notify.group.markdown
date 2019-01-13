---
layout: page
title: "Notify Group"
description: "Instructions on how to setup the notify group platform."
date: 2016-08-18 00:12
sidebar: true
comments: false
sharing: true
footer: true
logo: home-assistant.png
ha_category: Notifications
ha_release: 0.26
ha_qa_scale: internal
---

The `group` notification platform allows you to combine multiple `notify` platforms into a single service.

To use this notification platform in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
notify:
  - name: NOTIFIER_NAME
    platform: group
    services:
      - service: html5
        data:
          target: "macbook"
      - service: html5_nexus
```

{% configuration %}
name:
  description: Setting the parameter `name` sets the name of the group.
  required: true
  type: string
services:
  description: A list of all the services to be included in the group.
  required: true
  type: list
  keys:
    service:
      description: The service part of an entity ID, e.g. if you use `notify.html5` normally, just put `html5`. Note that you must put everything in lower case here. Although you might have capitals written in the actual notification services!
      required: true
      type: string
    data:
      description: A dictionary containing parameters to add to all notify payloads. This can be anything that is valid to use in a payload, such as `data`, `message`, `target` or `title`.
      required: false
      type: string
{% endconfiguration %}
