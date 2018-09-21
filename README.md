# Telegraf Config Collection
This is a basic repo aimed to share configuration blocks used in a Telegraf configuration. Various Configs will be outlined below. Keep in mind this may not cover all usage by all users, but it covers what I've been looking for and find useful to monitor.

# Core Configuration (telegraf.conf)
I've simply included this for 2 reasons:
1. To highlight the value of setting some of the core defaults to what suits your need. For example I've set the monitoring interval to 15s which is more aggressive than some may need. It can also be overidden on an agent basis. So for any specific section you can override these settings if needed.
2. Outline my usage of a very powerful technique, which is using the `tagpass` and `tagdrop` functionality. You'll notice extra lines at the bottom of many of my configs similar to:
```yaml
  [inputs.snmp.tags]
    influx_database = "telegraf_unifi"
```
What this does is allow me to place data into different databases within my InfluxDB or other outputs where perhaps I don't want to pile all data into one location. For this reason it's very valuable to filter my outputs using this mechanism and adding these tags to my data. The best part is, I've dropped these tags before recording them on the output, so there is no extra data to be concerned about storing that you don't need. This is done using the `tagexclude` functionality on the outputs.

# Ubiquiti Unifi via SNMP
The following configurations are useful for monitoring of Ubiquiti Unifi based networking hardware. SNMP is the quickest/easiest collection method without requiring extra scripting. These are broken out into 3 specific sub-configurations:
- UAP (Unifi Access Point)
- USG (Unifi Security Gateway)
- USW (Unifi Switch)


