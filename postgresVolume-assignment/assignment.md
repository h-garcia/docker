
## Database upgrade with containers???

We should be replacing the container with the new container db version

1. Create a postgres container with named volume psql-data using version 9.6.1
> Check the docker postgres documentation.. Check the tags tab and see from the different layers where the Volume address is...  
```
    docker container run -d --name postgres9.6.1 -v psql-data:/var/lib/postgresql/data postgres:9.6.1

    docker container logs -f postgres9.6.1 

    docker volume ls
```
2. Stop container, create a new postgres container with same named volume using 9.6.2  
```
    docker container stop postgres9.6.1 
    docker container run -d --name postgres9.6.2 -v psql-data://var/lib/postgresql/data postgres:9.6.2
```
3. Check logs, validate
```
    docker container logs -f postgres9.6.2
    docker volume ls
```

>>>> Profit!!!