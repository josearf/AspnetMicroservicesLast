# AspnetMicroservices
AspnetMicroservices

# UI Create new project with the src give and type ASPNet core api


# Generate docker
- right click catalogAPI project add orchestation -> docker-compose
- add mongodb
## in docker-compose
catalogdb:
    image: mongo

volumes:
    mongo_data:
## docker-compose-override
catalogdb:
    container_name: catalogdb
    restart: always
    ports:
      - "27017:27017"
    volumes:
      - mongo_data:/data/db

container_name: catalogapi
    - "DatabaseSettings:ConnectionString=mongodb://catalogdb:27017"
depends_on:
    - catalogdb
ports:
    - "8000:8080"

## for run
docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d