## Networking 


If you are wanting to use ingress, its probably better to use clusterIP instead

- I changed the UDP and TCP port to match the Mullvad ports allocated to me

![!Networking: qbittorrent](networking.png)

![!Networking: qbittorrent](networking_listening.png)

<br />

## Storage

### Configuration

The setup is default

![!Storage: NZBGet](storage_config.png)

### Data

I always mount to the root directory of the container

I also try to use the applications name for the mountpath, since its typically never going to be a file or folder thats already present 

![!Storage: NZBGet](storage_data.png)

<br />

## VPN

- Using a Wireguard setup
- Added the kubernetes network, as well as my LAN network to the killswitch
- Using a VPN for this application is in no way mandatory at all, I just simply felt safer transmitting data encrypted

![!Storage: NZBGet](vpn.png)

<br />