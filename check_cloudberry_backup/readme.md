# Check CloudBerry Backup
This **[Watchman Monitoring](https://www.watchmanmonitoring.com)** plugin checks if CloudBerry Backup for Mac (CBB) is installed, Licensed, and will warn or alert if the last backup is older than 3 days (default.)

This monitor has been tested and should be compatible with CloudBerry Backup for macOS v2.8 - v3.0.2.

_\_check\_cloudberry\_backup.plist_ is a plist file to define the plugin for Watchman Monitoring. It contains optional settings to configure how the plugin will alert Watchman Monitoring.

_\_check\_cloudberry\_backup.plugin_ is a python script that, by default, will send an alert to Watchman if CBB isn't installed, isn't licensed, a backup hasn't happend in the last 7 days, and send a warning if a backup hasn't happened in the last 3 days.

To install the plugin, simply copy the _\_check\_cloudberry\_backup.plist_ and _\_check\_cloudberry\_backup.plugin_ files into `/Library/MonitoringClient/Plugins`.

The plugins settings can be configured the CLI `defaults` command:

	sudo defaults write /Library/MonitoringClient/PluginSupport/_check_cloudberry_backup.plist

There are three settings that can be adjusted via the following keys:

* **should\_alert\_install**: BOOL This configures if Watchman should alert if CBB is installed.
* **backup\_warning**: INT This is the warning threshold in days.
* **backup\_alert**: INT This is the alert threshold in days.
