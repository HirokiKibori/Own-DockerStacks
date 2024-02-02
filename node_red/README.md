# PHP
A docker-compose for [node-red](https://nodered.org/).

Started with 
"[Docker Stack / Docker Compose](https://nodered.org/docs/getting-started/docker#docker-stack--docker-compose)"
and added directory *./data* to get control over configs, logs, ... .

**Only for development! Don't run this in a productive setup without editing before.**

Run command in root-directory:
```bash
docker-compose up
```

Open *node-red* with [localhost:1880](http://localhost:1880/)  

## Services
- **node-red (:1880)**: nodered/node-red:latest  
-> ./data

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

In the overlay-network you can connect by using the service-name. In my case '*node_red-node_red-1*'.