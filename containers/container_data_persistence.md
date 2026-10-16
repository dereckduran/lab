# Container are ephemeral
### Data is lost when the container is removed (updating the image, rebooting the host)

Docker solves by volume creation and mounting

Test it out with a Postgres database.

1. Make the volume
`docker volume create pg-data`

2. Run Postgres
```
docker run -d \
-e POSTGRES_PASSWORD=supersecretpassword \
-v pg-data:/var/lib/postgresql/data \
--restart=unless-stopped \
postgres:16
```

3. Wait for it to initialize ~5 seconds then test:
`docker ps`

4. Create the database
`docker exec mydb psql -U postgres -c "CREATE DATABASE testdb;"`

5. Verify it
`docker exec mydb -U postgres -c "\l"`

6. Remove the container
`docker rm -f mydb`

7. Make another container mounted at the same volume
```
docker run -d \
-e POSTGRES_PASSWORD=supersecretpassword \
-v pg-data:/var/lib/postgresql/data \
--restart=unless-stopped \
postgres:16
```

8. Check the data
`docker exec mydb -U postgres -c "\l"`

testdb should have appeared!

### Cleanup
```
docker rm -f mydb
docker volume rm pg-data
```
