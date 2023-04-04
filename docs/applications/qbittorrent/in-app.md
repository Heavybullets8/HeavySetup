## Downloads


??? qBittorrent "qBittorrent Configuration Settings" 
    | Setting                                      | Value                                  | Explanation                                                                    |
    |----------------------------------------------|----------------------------------------|--------------------------------------------------------------------------------|
    | Default Torrent Management Mode:             | Automatic                              | Automatically move files based on category                                     |
    | When Torrent Category changed:               | Relocate Torrent                       | Automatically move files based on category                                     |
    | When Default Save Path changed:              | Relocate Affected Torrents             | Automatically move files based on category                                     |
    | When Category Save Path changed:             | Relocate Affected Torrents             | Automatically move files based on category                                     |
    | Default Save Path:                           | `/media/download/torrent/complete`     | Set to your dataset mountpoint + `/complete`                                   |
    | Keep incomplete torrents in:                 | `/media/download/torrent/temp`         | Store incomplete torrents in a folder not monitored by apps                    |
    | Copy .torrent files for finished downloads to:| `/media/download/torrent/backup`      | Backup folder for all .torrent files in case of a crash                        |
    | Monitored Folder                             | `/media/download/torrent/monitor`      | Place .torrent files here to automatically start those torrents                |



![!Downloads: qbit](images/settings_downloads.png)

<br >

## Connection

This should equal to your listening port you set [during the installation](https://heavysetup.info/applications/qbittorrent/installation/#listening-ports)

![!Connection: qbit](images/settings_connection.png)

<br >

## Speed

- Set `Alternative Rate Limits` to `10000` KiB
    - This is so during the day, or when users are using my Plex server, my qBittorrent instance isn't using _ALL_ of my bandwidth seeding

- Set my schedule from `08:00` to `02:00`
    - 8am to 2am, which is around the time users are watching Plex

![!Speed: qbit](images/settings_speed.png)

<br >

## BitTorrent

- Disabled `Local Peer Discovery`
    - This is only useful if you are on a huge network, like a college campus or something like that


![!Speed: qbit](images/settings_bittorrent.png)

<br >

## WebGUI 

- Changed the password to something I would remember

Added both my LAN and Kubernetes LAN to the bypass list, this way neither of them have to authenticate, it gets annoying to log in over and over on your own network

**Bypass authentication for clients in whitelisted IP subnets**
```
192.168.0.0/16
172.16.0.0/16
```

![!Speed: qbit](images/settings_webgui1.png)

Since I am using `Traefik`, I decided to add the Kubernetes LAN to:

**Enable reverse proxy support**
```
172.16.0.0/16
```

![!Speed: qbit](images/settings_webgui2.png)


<br >

## Advanced


??? qBittorrent "qBittorrent Table + Explanation" 

    |          Setting           	                                        |         Value         |          Explanation                                	                                |
    |------------------------------------------------	                    |-----------------------|----------------------------------------------------------------------------------	    |
    | Network interface:                                                   	| `wg0` or `tun0`       | Bind this to `wg0` or `tun0` if you are using Wireguard (wg0) or Openvpn(tun0)        |
    | Optional IP address to bind to:                                      	| All Ipv4 Addresses 	| Kubernetes doesnt support ipv6 now anyway so, I set this to just ipv4               	|
    | Resolve peer countries:                                              	| True               	| Just so I can see what countries I am leeching/seeding from                         	|
    | Reannounce to all trackers when IP or port changed:                  	| True               	| In the event my IP or port changes, I want everyone to know, so I can seed or leech 	|

![!Speed: qbit](images/settings_advanced.png)

<br >