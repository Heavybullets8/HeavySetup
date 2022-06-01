## Networking 


If you are wanting to use ingress, its probably better to use clusterIP instead


### WebUI

Nothing changed here, this is just the port your app will use for its web service

![!Networking: qbittorrent](images/networking.png)

### Listening Ports

**These are the ports your other Syncthing service will connect to. You will need to either: **

??? VPN "If you are using a VPN"

    - Port forward this port on whatever VPN service you are using, as I have stated, I am using Mullvad
    - You only need to change the first TWO ports, not the last port

??? VPN "If you are NOT using a VPN"

    - Port forward this port on your router
    - Also, if you are NOT using a VPN you can leave the two ports default, the only reason I changed my port is because Mullvad does not give you the option to choose which port to use

![!Networking: qbittorrent](images/networking_listening.png)

<br />

## Storage

### Configuration

The setup is default

![!Storage: NZBGet](images/storage_config.png)

### Data

I always mount to the root directory of the container

I also try to use the applications name for the mountpath, since its typically never going to be a file or folder thats already present 

![!Storage: NZBGet](images/storage_data.png)

<br />

## VPN

- Using a Wireguard setup
- Added the kubernetes network, as well as my LAN network to the killswitch
- Using a VPN for this application is in no way mandatory at all, I just simply felt safer transmitting data encrypted

![!Storage: NZBGet](images/vpn.png)

<br />