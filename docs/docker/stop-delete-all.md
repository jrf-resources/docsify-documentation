# Stop and Delete Containers
How to stop all docker containers:
```bash
docker stop $(docker ps -a -q)
```
How to delete all docker containers:
```bash
docker rm $(docker ps -a -q)
```
