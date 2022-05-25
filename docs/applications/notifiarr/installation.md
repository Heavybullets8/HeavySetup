## Container

I use the big blue `Launch Docker Container` Button

![!Networking: NZBGet](images/launch-docker-image.png)

<br />

**Container Repository**

```
golift/notifiarr
```

**Container Tag**

```
latest
```

![!Networking: NZBGet](images/container.png)

<br />

## Networking

### DNS Settings

- I use the following setting so we can use the Kubernetes DNS names when linking applications together

![!Networking: NZBGet](images/networking.png)


### Port Forwarding

Container Port
```
54544
```
Node Port 
```
54544
```

Protocol
```
UDP
```
We cannot use Ports Lower than 9000, which is why I did not use the default `5454` port as suggested in their documentation
![!Networking: NZBGet](images/networking1.png)


<br />

## Storage

- It's important to set the mountpath as `/config`
- Set the path to the directory that contains your config file that you created in `Preparation`

![!Networking: NZBGet](images/storage_config.png)


<br />

## Ingress

### Purpose

We want to link `external services` to notifiarr so we can use a domain name when connecting their site to our client as shown:

![!Networking: NZBGet](images/networking_site.png)

### External Services

You will need to launch an `external services` application, offered by Truecharts

[External-Services Documentation](https://truecharts.org/manual/Quick-Start%20Guides/11-external-services/)

![!Networking: NZBGet](images/ingress.png)

### External Services Container

`External Service IP` is the local IP address of your Truenas SCALE server

`Service Port` is the [port used by Notifiarr](https://heavysetup.info/HeavySetup/applications/notifiarr/installation/#port-forwarding)
![!Networking: NZBGet](images/ingress-container.png)

### External Services Ingress

![!Networking: NZBGet](images/ingress-ingress.png)

<br />

## Security 

![!Networking: NZBGet](images/security.png)

<br />