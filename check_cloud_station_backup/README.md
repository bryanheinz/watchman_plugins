# Check Cloud Station Backup
Checks the last time Cloud Station Backup has backed up on a Mac.

_\_check\_cloud\_station\_backup.plist_ is a plist file to define the plugin for [Watchman Monitoring](https://www.watchmanmonitoring.com).

_\_check\_cloud\_station\_backup.plugin_ is a python script that will exit 0 and print the last backed up time if the last backup is less than 3 days, exit 20 if the last backup is older than 3 days, and finally exit 2 if the last backup is older than 7 days (which will trigger an email alert in Watchman.)
