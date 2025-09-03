# Grafana
A docker-compose for [Grafana](https://grafana.com/).


An guide can be found on [Run Grafana Docker image](https://grafana.com/docs/grafana/latest/setup-grafana/installation/docker/).

**Only for development! Don't run this in a productive setup without editing before.**

Run command in root-directory (for enterprise version):
```bash
docker-compose up -d
```

Run command in root-directory (for open-source version):
```bash
docker-compose -f .\compose-oss.yml up -d
```

Open *grafana* with [localhost:3000](http://localhost:3000/)  

Default login is:
- user: admin
- pw: admin

## Services
- **grafana-enterprise (:3000)**: grafana/grafana-enterprise:latest  
-> ./grafana-enterprise-storage

## ! Note !
This compose uses an external network (*public-test-network*) to connect to services in other docker-stacks.  
You need to create this before running '*docker-compose up*'.

A simple way to create the 'public-test-network' (bridge) is:
```bash
docker network create public-test-network
```

If you didn't created a swarm and want to create one in your docker environment, run:
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

In the overlay-network you can connect by using the service-name. In my case '*grafana-grafana_enterprise*'.