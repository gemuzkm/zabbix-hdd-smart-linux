# Scripts and template for monitoring SMART parameters with zabbix (zabbix_agent).

## Requirements:

- smartmontools (smartctl)
- zabbix-get (zabbix_get)
- zabbix-sender (zabbix_sender)

## Create a folder

```
mkdir /etc/zabbix/scripts/
```

## Copy file. Disk autodiscovery script:

/etc/zabbix/scripts/drives.discovery

## Make the file executable:

```
chmod +x /etc/zabbix/scripts/drives.discovery
```

## Add custom drives.discovery parameter to zabbix-agent:

```
echo "UserParameter=drives.discovery, /etc/zabbix/scripts/drives.discovery" > /etc/zabbix/zabbix_agentd.d/userparameter_drives.discovery.conf
```

## Restart zabbix-agent (option depends on your system)
```
systemctl restart zabbix-agent
```

or

```
/etc/init.d/zabbix-agent restart
```

## Copy files. Scripts to send smart parameters to zabbix-server:

/etc/zabbix/scripts/drives.drives.smart

/etc/zabbix/scripts/drives.smart.temperature

## Make the files executable:

```
chmod +x /etc/zabbix/scripts/drives.drives.smart
```

```
chmod +x /etc/zabbix/scripts/drives.smart.temperature
```

## Add scripts to the cron run (drives.smart every hour, drives.smart.temperature every minute):

```
1 */1 * * * root /etc/zabbix/scripts/drives.smart
*/1 * * * * root /etc/zabbix/scripts/drives.smart.temperature
```

## Template for zabbix server

You need to import the template and add it to the desired host.

Path: Template for zabbix\Template_HDD-SMART-LINUX.xml

[Source link](https://valynkin.ru/monitoring-smart-zhestkih-diskov-v-linux-pri-pomoshi-zabbix.html). Corrected errors in source files. Workability tested on RHEL 6.10.