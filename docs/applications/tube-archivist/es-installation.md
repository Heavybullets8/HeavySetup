For this application I used the `Custom-App` provided by [TrueCharts](https://truecharts.org/manual/Quick-Start%20Guides/01-Adding-TrueCharts/).

- Available under the `stable` train

![!Container: Tube](images/custom-app.png)

<br />

## Container 

**Application Name**
```
ta-elastic
```
The name is very important, as it determines our DNS names, which is how we are going to connect the applications together..

You don't HAVE to follow my naming scheme, but if you don't, you'll have to also change your DNS name

**Container Repository**
```
bbilly1/tubearchivist-es
```
**Container Tag**
```
latest
```

![!Container: Tube](images/es-container.png)

<br />

## Environment Variables

**Name**
```
xpack.security.enabled
```
**Value**
```
true
```
<br />

**Name**
```
ELASTIC_PASSWORD
```
**Value**
```
verysecret
```

![!env1: Tube](images/es-env1.png)

**Name**
```
discovery.type
```
**Value**
```
single-node
```

<br />

**Name**
```
ES_JAVA_OPTS
```
**Value**
```
-Xms512m -Xmx512m
```

![!env1: Tube](images/es-env2.png)

<br />


## Networking

**Target Port**
```
9200
```
**Port**
```
9200
```

![!Networking: Tube](images/es-networking.png)

<br />

## Storage

- I am using PVC in this case since this is not something the user will need to interact with 

Ensure the mountpath is:
```
/usr/share/elasticsearch/data
```

Elasticsearch specifically looks to that mount point, its required

![!Storage: Tube](images/es-storage.png)


<br />

## Security

Running the application without user:group `0` or `root`, resulted in the container not starting.

![!Storage: Tube](images/es-security1.png)

- Also, in this case, `fsgroup` was also required to be `0`

![!Storage: Tube](images/es-security2.png)

<br />