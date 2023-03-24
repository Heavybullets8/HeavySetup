For this application I used the `Custom-App` provided by [TrueCharts](https://truecharts.org/manual/Quick-Start%20Guides/01-Adding-TrueCharts/).

- Available under the `stable` train

![!Container: Tube](images/custom-app.png)

<br >



## Container

I am using the `hotio/sonarr` container

I also am using the `v4` tag, which is the latest version of Sonarr

![!Networking: qbittorrent](images/container.png)

<br />

## Networking 

I personally use clusterIP, because I use ingress for all of my applications

- You may want to keep this on LoadBalancer, if you are not using ingress

![!Networking: qbittorrent](images/networking.png)

<br />

## Storage

### Configuration

The setup is default

![!Storage: NZBGet](images/storage_config.png)

<br >

### Media

- media is the dataset I created for my media here: [Dataset Creation](https://heavysetup.info/general_guides/folder_structure/dataset/)
- media is also the dataset that hosts all nested folders for my media, as shown in the tree structure here: [Folder Structure](https://heavysetup.info/general_guides/folder_structure/about/#tree)
- Since Sonarr will need to see all of the sub folders within media, I gave it access to the parent dataset

![!Storage: NZBGet](images/storage_data_media.png)

<br >

### Backups

- '/config/Backups' is the location Radarr places its automatic and manual backups
- I created a separate dataset meant for backups, specifically to have an easy way to restore a backup, in the event the application is wrongly deleted, or removed, corrupt, whatever

![!Storage: NZBGet](images/storage_data_backups.png)

<br >


## Permissions

Again, you can bypass this step if you use the regular Truecharts version of the Sonarr application

![!Storage: NZBGet](images/security_and_perms.png)

![!Storage: NZBGet](images/security_user_group.png)

<br />