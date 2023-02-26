For this application I used the `Custom-App` provided by [TrueCharts](https://truecharts.org/manual/Quick-Start%20Guides/01-Adding-TrueCharts/).

- Available under the `stable` train

![!Container: Tube](images/custom-app.png)

<br />

### Container

**Container Repository**

```
golift/notifiarr
```

**Container Tag**

```
latest
```

![!Container: Notifiarr](images/container.png)

<br />

## Environment Variables

**Name**
```
DN_API_KEY
```
**Value**
```
API_KEY_FROM_NOTIFIARR.COM
```

??? picture "API Key Location"
    [Link to Notifiarr Profile Page](https://notifiarr.com/user.php?page=profile "Click to visit the profile page") 
    ![](images/profile.png)

<br >

**Name**
```
DN_UPSTREAMS_0
```
**Value**
```
172.16.0.0/16
```
> This is the default range of the kubernetes network for TrueNAS SCALE

> You also can add your local network range here as well

![!ENVVAR: Notifiarr](images/env_vars.png)


<br />

## Networking

**Target Port**
```
5454
```

**Port**
```
5454
```

![!Networking: Notifiarr](images/networking.png)

<br >


## Ingress

> This is optional, but I recommend it. It is a lot better than using the port forwarding method.

![!Networking: Notifiarr](images/ingress-ingress.png)

<br />

## Storage

Here we are just going to make two Persistent Volumes. One for the config and one for utmp.

**Mount Path**
```
/config
```

**Mount Path**
```
/var/run/utmp
```

![!Networking: Notifiarr](images/storage.png)


<br >

## Username and Password

### Find your credentials

> After you click save, the container will deploy for the first time. you absolutely need to check the logs, because your username and password will be in there. 


View your logs
![!Networking: Notifiarr](images/view_logs.png)


Copy your username and password
![!Networking: Notifiarr](images/username_password.png)


### Set your credentials


> After you have your username and password, you can change them in the WebGUI if you want.


![!Networking: Notifiarr](images/reset_password.png)
