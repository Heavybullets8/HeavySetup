## Purpose

I personally use this to:

Sync media from my Seedbox to my local Truenas SCALE server and vice versa.

1. Movie/Series requests are sent from Radarr/Sonarr to my Seedbox
2. After the torrents are complete, they are moved to a folder Syncthing is monitoring
3. Syncthing (on my seedbox), will communicate with Syncthing (on my Truenas SCALE server), notifying it of new files
4. A connection will establish, and the files will be transferred to my Truenas SCALE server
5. After the syncronization is complete, Sonarr/Radarr will see a new completed file in the Syncthing folder
6. Sonarr/Radarr will pull that file from the completed folder into my `media` folder, where Plex can finally see it


<br >

## Sources

#### [Website](https://syncthing.net/)

Important information regarding Syncthing


<br >

#### [Github](https://github.com/syncthing/syncthing)

Source code for the project, active issues etc. 

