# Scripts and template for monitoring SMART parameters with zabbix (zabbix_agent).

## Requirements:

- smartctl
- zabbix_agent
- zabbix_sender

## Create a disk autodiscovery script:

/etc/zabbix/scripts/drives.discovery

## Create scripts to send smart parameters to zabbix-server:

/etc/zabbix/scripts/drives.drives.smart
/etc/zabbix/scripts/drives.smart.temperature

## Add scripts to the cron run (drives.smart every hour, drives.smart.temperature every minute):

1 */1 * * * root /etc/zabbix/scripts/drives.smart
*/1 * * * * root /etc/zabbix/scripts/drives.smart.temperature

