# PHP
A docker-compose for [Eclipse Mosquitto™](https://www.mosquitto.org/).

Started with 
"[Quick reference](https://hub.docker.com/_/eclipse-mosquitto)"
and added *./mosquitto.conf* as well as directories *./data* and *./log* to get control over configs, logs, ... .  
The configuration possibilities are documented on the [mosquitto.conf man page](https://mosquitto.org/man/mosquitto-conf-5.html).  
The given *./mosquitto.conf* was created to test this broker with a default node-red instance.

An other guide can be found on [setup-mosquitto-with-docker](https://github.com/sukesh-ak/setup-mosquitto-with-docker).

**Only for development! Don't run this in a productive setup without editing before.**

Run command in root-directory:
```bash
docker-compose up
```

Open *eclipse-mosquitto* with [localhost:1883](http://localhost:1883/)  
Open *eclipse-mosquitto (websockets)* with [localhost:9001](http://localhost:9001/)  

## Services
- **eclipse-mosquitto (:1883 / :9001)**: eclipse-mosquitto:latest  
-> ./mosquitto.conf  
-> ./data  
-> ./log  

## ! Note !
This compose uses an external network (*public-test-network*) to connect to services in other docker-stacks.  
You need to create this before running '*docker-compose up*'.

If you didn't created a swarm in your docker environment, run:
```bash
docker swarm init
```
For more information read [the manual](https://docs.docker.com/engine/reference/commandline/swarm_init/).

To create the overlay-network '*public-test-network*', run:
```bash
docker network create -d overlay --attachable public-test-network
```

If you want to connect to this network with other services from other docker-stacks, define this network in your compose-file:
```
networks:
  public-test-network:
    external: true
```
and add this as *network* to your service you want to connect.