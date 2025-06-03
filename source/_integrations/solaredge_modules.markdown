---
title: SolarEdge Modules
description: Instructions on how to integrate SolarEdge Modules within Home Assistant.
ha_category:
  - Energy
ha_release: '2025.7'
ha_iot_class: Cloud Polling
ha_config_flow: true
ha_domain: solaredge_modules
ha_dhcp: true
ha_codeowners:
  - '@tronikos'
ha_integration_type: service
---

The SolarEdge integration allows you to get energy production per inverter/string/module from your SolarEdge solar power setup and insert them into Home Assistant statistics.

You can find the created statistics in **Developer Tools** > **Statistics** and searching for `solaredge_modules`.
You can show them in the UI using the **Statistic** or **Statistics graph** cards.
You can use them in automations using the **SQL** integration.

The main use case is to track your solar production per module in order to identify any faulty module that underperforms and might need cleaning or repairing.

The integration fetches energy production for the past 7 days every 12 hours and inserts the data into statistics.

To setup the integration you need your username/password that has access to the [SolarEdge web portal](https://monitoring.solaredge.com/). You also need the site ID which you can get from the URL once you log-in, e.g. `1234` for `https://monitoring.solaredge.com/solaredge-web/p/site/1234/`

{% include integrations/config_flow.md %}

## Removing the integration

{% include integrations/remove_device_service.md %}

## Known limitations

- The integration intentionally doesn't create any sensors. All data is only available in statistics.
- The statistics are intentionally updated infrequently. If you want more frequent updates you can call `homeassistant.reload_config_entry` from an automation.

## Troubleshooting

Make sure your account has access to the [SolarEdge web portal](https://monitoring.solaredge.com/) and that you can access the **Layout** tab there. If not, you will have to ask your installer to give you access to it.
