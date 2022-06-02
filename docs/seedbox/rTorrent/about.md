## rTorrent vs ruTorrent

rTorrent is a command line bittorrent client

ruTorrent is a web interface for rTorrent
> For now on I will simply be referring to them as one, under the name of just **_rTorrent_** for simplicity



## Why I use rTorrent

Unless you can download qBit Manage for qBittorrent (which in many cases you cant)

rTorrent is simply the best seedbox bittorrent client, heres why:

- Supports hard links

??? why "Why this is important"
    Instead of copying or moving a file, Hard links allow us to create a "link" back to the original folder.

    Which is useful because we don't want to constantly be moving or even worse, copying files each time they finish just so Syncthing can see them.

    Instead, we'll create a VERY lightweight hard link, that point back to the original folder. 

    So once files are finished downloading, they will create this lightweight hard link in the folder syncthing can see, so then it can start sending the linked files back to our Truenas SCALE server. After Sonarr/Radarr import those files, and the cron job we created in the syncthing section has ran, the link will be broken. Which is fine, because the torrent files will still be seeding, and the media will now be on our Plex server. 

- Per-Tracker ratio rules

??? why "Why this is important"
    Some trackers are ratioless, (meaning they do not require you seed to a given ratio before you are free to stop seeding)

    And some *are* ratio based, (meaning you have to seed the torrent to a certain percentage or value for you to be free to stop seeding)

    Well, if you're using ANY other Bittorent client, you dont have the option to set certain trackers to seed to a certain ratio, or to a certain time.

    If your bittorrent client pre-maturely deletes or stops a torrent file before that trackers requirements are met, then it could land you in trouble with that private tracker, and possibly get you kicked from a site. 
