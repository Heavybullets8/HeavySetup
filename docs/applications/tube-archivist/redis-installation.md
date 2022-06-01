For this application I used the `Custom-App` provided by [TrueCharts](https://truecharts.org/manual/Quick-Start%20Guides/01-Adding-TrueCharts/).

- Available under the `stable` train

![!Container: Tube](images/custom-app.png)

<br />

## Container 

**Application Name**
```
ta-redis
```
The name is very important, as it determines our DNS names, which is how we are going to connect the applications together..

You don't HAVE to follow my naming scheme, but if you don't, you'll have to also change your DNS name


**Container Repository**
```
redislabs/rejson
```
**Container Tag**
```
latest
```

![!Container: Tube](images/redis-container.png)

<br />


## Networking

**Target Port**
```
6379
```
**Port**
```
6379
```

![!Networking: Tube](images/redis-networking.png)

<br />

## Storage

- I am using PVC in this case since this is not something the user will need to interact with 

Ensure the mountpath is:
```
/data
```

Redis specifically looks to that mount point, its required

![!Storage: Tube](images/redis-storage.png)


<br />

## Security

This application runs fine with default permissions

![!Storage: Tube](images/redis-security.png)

<br />