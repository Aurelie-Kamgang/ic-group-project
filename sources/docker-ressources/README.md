### deploy odoo

- prerequisite: install docker-compose 
- odoo is accessible on port 8069 and postgress in 5432
- odoo and db containers are in odoo_network of type bridge 
- To start your Odoo instance, go in the directory of the `docker-compose.yml` and run : `console
docker-compose up -d`
- To see if the containers are running:`docker-compose ps`

### deploy pgadmin

- prerequisite: install docker-compose 
- pgadmin is accessible on port 5050
- pgadmin is ic_network_pgadmin of type bridge 
- To start your pgadmin instance, go in the directory of the `docker-compose.yml` and run : `console
docker-compose up -d`
- To see if the containers are running:`docker-compose ps`

### deploy ic_webapp

- prerequisite: install docker-compose 
- ic_webapp is accessible on port 8080
- ic_webapp is ic_network_webapp of type bridge 
- To start your ic_webapp instance, go in the directory of the `docker-compose.yml` and run : `console
docker-compose up -d`
- To see if the containers are running:`docker-compose ps`

### deploy all_stack

- prerequisite: install docker-compose 
- ic_webapp is accessible on port 8080 and odoo in port 8069
- ic_webapp and odoo are in ic_network network of type bridge 
- To start your ic_webapp and odoo instance, go in the directory of the `docker-compose.yml` and run : `console
docker-compose up -d`
- To see if the containers are running:`docker-compose ps`
