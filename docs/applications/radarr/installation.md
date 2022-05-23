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