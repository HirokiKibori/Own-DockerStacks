# PHP
A docker-compose for [hoppscotch](https://github.com/hoppscotch/hoppscotch).

Started with 
"[Install and build](https://docs.hoppscotch.io/documentation/self-host/community-edition/install-and-build)"
and added postgres to run hoppscotch.

**Only for development! Don't run this in a productive setup without editing before.**

Run command in root-directory:
```bash
docker-compose up
```

Open *hoppscotch* with [localhost:3000](http://localhost:3000/)  
Open *admin* with [localhost:3100](http://localhost:3100/)  
Open *backend* with [localhost:3170](http://localhost:3170/)

## Services
- **postgres**: postgres:latest  
-> ./postgresql_data
- **hoppscotch-backend (:3170)**: hoppscotch/hoppscotch-backend:latest
- **hoppscotch-admin (:3100)**: hoppscotch/hoppscotch-admin:latest
- **hoppscotch-frontend (:3000)**: hoppscotch/hoppscotch-frontend:latest