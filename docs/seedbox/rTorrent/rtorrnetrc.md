## Configuration

I will only be covering the most important stuff in this section.. but you can still expand my whole config file below.


| Name                      	| Value                                       	| Reason                                                                                                                                                                                                 	|
|---------------------------	|---------------------------------------------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| `network.port_range.set`  	| `62000-62000`                               	| This is not mandatory. But I wanted to set a static port because I have Uptime Kuma consistently pinging this port to see if rTorrent is up. In the event rTorrent crashes, Uptime Kuma will notify me. 	|
| `network.port_random.set` 	| `no`                                        	| Same reason as above                                                                                                                                                                                   	|
| `directory.default.set`   	| `/home/USERNAME/downloads/rtorrent/seeding` 	| This is the folder I want my files to be moved to once completed Note: This is NOT the Hard Link location we will be setting later. So you need to ensure those two locations are different.           	|

Also note 

- number of peers - global slots
- per torrent connection maximums, in progress
- per torrent connection maximums, seeding
- per torrent active downloads/uploads

I changed the values under those catagories to be huge. You may need to set yours lower. But since my box is ONLY seeding torrents, I wanted to make sure it was doing just that.

??? rtorrentrc "rtorrent.rc"
    ```
    #################################################
    ## These settings are mostly user customizable ##
    #################################################

    ## These control where rTorrent looks for .torrents and where files are saved
    directory.default.set = /home/USERNAME/downloads/rtorrent/seeding

    schedule2 = watch_directory,5,5,load.start=~/watch/rtorrent/*.torrent
    #schedule2 = untied_directory,5,5,close_untied=

    # If there's less than 256MB of disk space, it will stop torrents from
    # downloading.  Keep in mind that we receive alerts about low disk space, so
    # it shouldn't actually get this low.  However, if the server runs out of space,
    # all of the rTorrents will lock up, eating all of the CPU and spiking loads.
    schedule2 = low_diskspace,5,60,close_low_diskspace=5120M

    trackers.use_udp.set = yes
    # Upload/download rate in KB/s. 0 for unlimited
    throttle.global_down.max_rate.set_kb = 0
    throttle.global_up.max_rate.set_kb = 0

    # number of peers - global slots
    throttle.max_downloads.global.set = 150
    throttle.max_uploads.global.set   = 5000

    # per torrent connection maximums, in progress
    throttle.min_peers.normal.set = 5000
    throttle.max_peers.normal.set = 5000

    # per torrent connection maximums, seeding
    throttle.min_peers.seed.set = 5000
    throttle.max_peers.seed.set = 5000

    # per torrent active downloads/uploads
    throttle.max_uploads.set = 5000
    throttle.max_downloads.set = 5000

    #################################################
    ## These settings shouldn't need to be changed ##
    #################################################
    network.scgi.open_local = ~/.config/rtorrent/socket
    session.path.set = ~/.config/rtorrent/session

    encoding.add = UTF-8
    network.port_range.set = 62000-62000
    network.port_random.set = no
    network.http.dns_cache_timeout.set = 0
    ##network.http.ssl_verify_peer.set = 0
    ##network.http.ssl_verify_host.set = 0
    protocol.encryption.set = allow_incoming,enable_retry,try_outgoing

    # This chmods the downloaded files to 770.  This will allow them to be deleted
    # by w/ruTorrent, while not allowing any other users to touch them.
    system.umask.set = 007

    # XMLRPC Size Limit
    network.xmlrpc.size_limit.set = 16M
    system.file.max_size.set = 1024G

    method.set_key = event.download.resumed,foo,"execute.nothrow=rtcheck,$d.name=,$d.hash="
    method.set_key = event.download.finished,foo2,"execute.nothrow=rtcheck,$d.name=,$d.hash="
    method.set_key = event.download.finished,filebot,"execute.nothrow={.filebot/scripts-enabled/rtorrent-postprocess.sh,$d.base_path=,$d.name=,$d.custom1=}"
    #debug method.set_key = event.download.finished, finished_try, "print=finished-triggered!"

    pieces.hash.on_completion.set = no
    dht.mode.set = off
    pieces.memory.max.set = 4096M
    protocol.pex.set = no
    pieces.preload.type.set = 1
    pieces.preload.min_size.set = 1
    pieces.preload.min_rate.set = 1
    #ruTorrent plugins
    schedule2 = init_plugins, 10, 0, "execute2 = {sh,-c,/usr/bin/php ~/www/rutorrent/php/initplugins.php &}"
    ```

## rtorrent.rc Save Location

This again, is dependant on your seedbox. Mine was in `home/.config/rtorrent/rtorrent.rc`

<br >