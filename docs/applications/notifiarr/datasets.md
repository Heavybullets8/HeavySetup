## Config File

So, this isn't as easy as just taking screenshots.. 

You'll need to go to Notifiarrs site, and look at [their documentation](https://notifiarr.wiki/en/Client/Configuration) as well

Ensure the config file is named: 

```
notifiarr.conf
```

Here is a template that I use:

- Note I do not use Lidarr, or anything else, so this is a very slimmed down version of the configuration file

```
###############################################
# Notifiarr Client Example Configuration File #
# Created by Notifiarr v0.2.0   @ 212410T2154 #
###############################################

# This API key must be copied from your notifiarr.com account.
api_key = "NOTIFIARR_API_KEY_HERE"

## The ip:port to listen on for incoming HTTP requests. 0.0.0.0 means all/any IP and is recommended!
## You may use "127.0.0.1:5454" to listen only on localhost; good if using a local proxy.
## This is used to receive Plex webhooks and Media Request commands.
##
bind_addr = "0.0.0.0:80"

## This application can update itself on Windows systems.
## Set this to "daily" to check GitHub every day for updates.
## You may also set it to a Go duration like "12h" or "72h".
## THIS ONLY WORKS ON WINDOWS
auto_update = "off"

## Quiet makes the app not log anything to output.
## Recommend setting log files if you make the app quiet.
## This is always true on Windows and macOS app.
## Log files are automatically written on those platforms.
##
quiet = true
debug = false
debug_log = '/config/debug.log'

## All API paths start with /api. This does not affect incoming /plex webhooks.
## Change it to /somethingelse/api by setting urlbase to "/somethingelse"
##
urlbase = "/"

## Allowed upstream networks. The networks here are allowed to send x-forwarded-for.
## Set this to your reverse proxy server's IP or network. If you leave off the mask,
## then /32 or /128 is assumed depending on IP version. Empty by default. Example:
##
upstreams = [ "172.16.0.0/12" ]

##
## Set this to the number of megabytes to rotate files.
log_file_mb = 100
##
## How many files to keep? 0 = all.
log_files = 0
##
## Unix file mode for new log files. Umask also affects this.
## Missing, blank or 0 uses default of 0600. Permissive is 0644. Ignored by Windows.
file_mode = "0600"

## Web server and application timeouts.
##
timeout = "1m0s"


##################
# Starr Settings #
##################

## The API keys are specific to the app. Get it from Settings -> General.
## Configurations for unused apps are harmless. Set URL and API key for
## apps you have and want to make requests to using Media Bot.
## See the Service Checks section below for information about setting the names.
##
## Examples follow. UNCOMMENT (REMOVE #), AT MINIMUM: [[header]], url, api_key

[[radarr]]
name      = "Radarr" # Set a name to enable checks of your service.
url       = "http://radarr.ix-radarr.svc.cluster.local:7878"
api_key   = "RADARR_API_KEY_HERE"


[[sonarr]]
name      = "Sonarr"  # Set a name to enable checks of your service.
url       = "http://sonarrnll-custom-app.ix-sonarrnll.svc.cluster.local:8989"
api_key   = "SONARR_API_KEY_HERE"


#################
# Plex Settings #
#################

## Find your token: https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/
##
[plex]
  url     = "http://plex.ix-plex.svc.cluster.local:32400" # Your plex URL
  token   = "PLEX_TOKEN_HERE" # your plex token; get this from a web inspector


##################
# Service Checks #
##################

## This application performs service checks on configured services at the specified interval.
## The service states are sent to Notifiarr.com. Failed services generate a notification.
## Setting names on Starr apps (above) enables service checks for that app.
## Use the [[service]] directive to add more service checks. Example below.

[services]
  disabled = false   # Setting this to true disables all service checking routines.
  parallel = 1       # How many services to check concurrently. 1 should be enough.
  interval = "10m0s" # How often to send service states to Notifiarr.com. Minimum = 5m.
  log_file = ''      # Service Check logs go to the app log by default. Change that by setting a services.log file here.


```

<br />

## Dataset Permissions

After you have created your `notifiarr.conf` file, and filled out the required fields, you will need to create a dataset for the file to reside in

![!Networking: NZBGet](storage_permissions.png)

<br />