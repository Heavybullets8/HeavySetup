## Networking 

### WebGUI

I left this default since there was no reason for me to change the WebGUI port

This is ALSO the port Sonarr/Radarr and other services will use to connect to qBittorrent

![!Networking: qbittorrent](images/networking_webgui.png)


### Listening Ports

??? VPN "With VPN"
    - No need to port forward on your router
    - If you want fast seeding, you will need a service that supports port forwarding
    - I use Mullvad, and changed the port below to the port that was allocated to me by Mullvad

??? NOVPN "Without VPN"
    - You can leave the port default without a VPN
    - If you want fast seeding though, you will need to port forward this port on your router

![!Networking: qbittorrent](images/networking_listening.png)

<br />

## Storage

### Configuration

The setup is default

![!Storage: NZBGet](images/storage_config.png)

### Data

- media is the dataset I created for my media here: [Dataset Creation](https://heavysetup.info/general_guides/folder_structure/dataset/)
- media is also the dataset that hosts all nested folders for my media, as shown in the tree structure here: [Folder Structure](https://heavysetup.info/general_guides/folder_structure/about/#tree)
- Qbittorrent only needs to access the `/media/download/torrent` folder, so I gave it access to that folder only
- Sonarr/Radarr will be able to hardlink files from the download directory, since they both will be seeing the folders they require


![!Storage: NZBGet](images/storage_data.png)

<br />

## VPN

- Using a Wireguard setup
- Added the kubernetes network, as well as my LAN network to the killswitch

![!Storage: NZBGet](images/vpn.png)

<br />