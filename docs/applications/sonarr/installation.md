For this application I used the `Custom-App` provided by [TrueCharts](https://truecharts.org/manual/Quick-Start%20Guides/01-Adding-TrueCharts/).

- Available under the `stable` train

![!Container: Tube](images/custom-app.png)

<br >



## Container

So, this is going to be a bit different, but I actually use custom-app for this application

At the time of creating this application, I needed the additional features only available in the nightly version of the application

However, you would probably be fine setting this up like the Radarr setup (using the regular Truecharts version), as the enhancements are now apart of the stable image

![!Networking: qbittorrent](images/container.png)

<br />

## Networking 

If you are wanting to use ingress, its probably better to use clusterIP instead

- I changed the UDP and TCP port to match the Mullvad ports allocated to me

![!Networking: qbittorrent](images/networking.png)

<br />

## Storage

### Configuration

The setup is default

![!Storage: NZBGet](images/storage_config.png)

<br >

### Media - Destination Folders

- Media is so that Radarr will have a location to place files once they're completed
- This will be the folder Radarr places files for plex to then parse through.

![!Storage: NZBGet](images/storage_data_media.png)

<br >

### Backups

- '/config/Backups' is the location Radarr places its automatic and manual backups
- I created a separate dataset meant for backups, specifically to have an easy way to restore a backup, in the event the application is wrongly deleted, or removed, corrupt, whatever

![!Storage: NZBGet](images/storage_data_backups.png)

<br >

### NZB 

- This is obviously the location Radarr will look for completed NZB files
- Its also the location NZBGet saves its completed movie files

![!Storage: NZBGet](images/storage_data_nzb.png)

<br >

### Bittorrent 

- This is the location Radarr will look for completed qBittorrent files
- Its also the location qBittorrent saves its completed movie files

![!Storage: NZBGet](images/storage_data_qbit.png)

<br >

### Syncthing

- This is the location Radarr will look for completed Syncthing files
- Its also the location Syncthing saves its completed movie files

![!Storage: NZBGet](images/storage_data_syncthing.png)

<br />

## Permissions

Again, you can bypass this step if you use the regular Truecharts version of the Sonarr application

![!Storage: NZBGet](images/security_and_perms.png)

![!Storage: NZBGet](images/security_user_group.png)

<br />