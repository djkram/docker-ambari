# Ambari on Docker

This projects aim is to help you to get started with Ambari.

## CLone Project
```
git clone https://github.com/djkram/docker-ambari.git

cd docker-ambari
```

## Install Docker

Follow the description at the docker getting started page for your appropriate OS: ([Linux](http://docs.docker.com/linux/started/), [Mac](http://docs.docker.com/mac/started/), [Windows](http://docs.docker.com/windows/started/))

## Starting containers

This will start (and download if you never used it before) an image based on
Centos 7 with pre-installed Ambari 2.2.0 ready to install HDP 2.3.

This git repository also contains an ambari-functions script
which will launch all the necessary containers to create a fully functional cluster. Download the file and source it:

For Windows:

```
. ambari-functions or source ambari-functions
```

For Mac & linux:

```
source ambari-functions
```

Now you can issue commands with `amb-`prefix like:
```
amb-settings
```
To start a 3 node cluster:
```
amb-start-cluster 3
```
It will launch containers like this (1 Ambari server 2 agents 1 consul server):
```
CONTAINER ID        IMAGE                          COMMAND                  STATUS              NAMES
52b563756d26        hortonworks/ambari-agent       "/usr/sbin/init syste"   Up 9 seconds        amb2
ddfc8f00d30a        hortonworks/ambari-agent       "/usr/sbin/init syste"   Up 10 seconds       amb1
ca87a0fb6306        hortonworks/ambari-server      "/usr/sbin/init syste"   Up 12 seconds       amb-server
7d18cc35a6b0        sequenceiq/consul:v0.5.0-v6   "/bin/start -server -"    Up 17 seconds       amb-consul
```

Now you can reach the Ambari UI on the amb-server container's 8080 port. Type the `amb-settings` for IP:
```
amb-settings
...
AMBARI_SERVER_IP=172.17.0.17
```

## Cluster deployment 

Once the container is running, you can deploy a cluster. Instead of going to
the webui, we can use ambari-shell, which can interact with ambari via cli,
or perform automated provisioning. 

```
amb-deploy-cluster
```



## Ambari Multi-node Hadoop cluster on Google Cloud
https://github.com/GoogleCloudPlatform/bdutil/blob/master/platforms/hdp/README.md


