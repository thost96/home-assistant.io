---
title: "Common tasks - Container"
description: "Common tasks for Home Assistant Container"
installation: container
---

## Backup

To learn how to back up the system or how to restore a system from a backup, refer to the backup documentation under [common tasks](/common-tasks/general/#backups).

## Update

{% include common-tasks/update.md %}
{% include common-tasks/specific_version.md %}
{% include common-tasks/beta_version.md %}
{% include common-tasks/development_version.md %}

## Configuration check

After changing configuration files, check if the configuration is valid before restarting Home Assistant Core.

_If your container name is something other than `homeassistant`, change that part in the examples below._

Run the full check:

```bash
docker exec homeassistant python -m homeassistant --script check_config --config /config
```

Listing all loaded files:

```bash
docker exec homeassistant python -m homeassistant --script check_config --files
```

Viewing an integration’s configuration ([`light`](/integrations/light) in this example):

```bash
docker exec homeassistant python -m homeassistant --script check_config --info light
```

Or all integrations’ configuration

```bash
docker exec homeassistant python -m homeassistant --script check_config --info all
```

You can get help from the command line using:

```bash
docker exec homeassistant python -m homeassistant --script check_config --help
```
