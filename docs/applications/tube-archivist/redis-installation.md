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
redis/redis-stack-server
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
> ClusterIP is being used since no other services besides TA will be accessing this container, so the port only needs to be exposed within the kubernetes network. 
<br />

## Storage

- I am using PVC in this case since this is not something the user will need to interact with 

Ensure the mountpath is:
```
/data
```

Redis specifically looks to that mount point, its required

![!Storage: Tube](images/redis-storage.png)
> You of course can change `Size Quotum of Storage` to something lower. I cannot though. I would recommend setting it to something a bit lower. You will receive a notification on Truenas if your PVC is filling up, so you can expand the size, but you cannot EVER retract to a lower size later on. 

<br />

## Security

This application runs fine with default permissions

![!Storage: Tube](images/redis-security.png)

<br />