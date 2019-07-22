# Check MDM
Checks the enrollment status of MDM on a Mac and reports it to **[Watchman Monitoring](https://www.watchmanmonitoring.com)**.

_\_check\_mdm.plist_ is a plist file to define the plugin for Watchman Monitoring. It contains optional settings to configure how the plugin will alert Watchman Monitoring.

_\_check\_mdm.plugin_ is a python script that, by default, will exit cleanly if the Mac is enrolled in MDM and it's user-approved, exit with a once-a-day alert if not enrolled in MDM, and exit with an alert every time the agent is run if the Mac is enrolled in MDM but isn't user approved (10.13.4+ only.)

To install the plugin, simply copy the _\_check\_mdm.plist_ and _\_check\_mdm.plugin_ files into `/Library/MonitoringClient/Plugins`.

After installing and running for the first time the alert settings can be configured in System Preferences -> Monitoring Client -> Settings -> Check MDM.

Alternatively the settings can be configured with the CLI `defaults` command:

  sudo defaults write /Library/MonitoringClient/PluginSupport/_check_mdm_settings.plist KEY -int N

There are two keys:

* **mdm_warning**: which configures the MDM enrollment alert.
* **uamdm_warning**: which configures the MDM user approval alert (10.13.4+ only.)

Both keys (KEY) take the following integer values (N): 0 == None, 1 == Warn, 2 == Alert.

* **None**: will only show an alert in Watchman Monitoring.
* **Warn**: will show an alert in Watchman Monitoring and send an email alert once a day.
* **Alert**: will show an alert in Watchman Monitoring and will send an email alert every time Watchman Monitoring is run on the Mac.
