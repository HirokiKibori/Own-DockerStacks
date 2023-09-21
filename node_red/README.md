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