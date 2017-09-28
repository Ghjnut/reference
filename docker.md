DOCKER
------
## Management

#### Delete all containers
`docker rm $(docker ps -aq)`
#### Delete all images
`docker rmi $(docker images -q)`
#### Delete orphaned images
`docker rmi $(docker images -q -f dangling=true)`

#### Stop all containers, remove all images
`docker ps -aq |xargs docker stop; docker images -q |xargs docker rmi`

#### Backup volumes
`sudo docker run --rm --volumes-from DATA -v $(pwd):/backup busybox tar cvf /backup/backup.tar /data`

`docker ps -a -q |xargs docker stop; docker ps -a -q |xargs docker rm -fv; docker images -q |xargs docker rmi;`

#### Remove containers base on newest
`docker rm $(docker ps -aq |head -n 1)`

#### Remove images base on newest
`docker rmi $(docker images -q |head -n 1)`

#### Remove untagged images
`docker rmi $(docker images |grep \<none\> |awk '{print $3}')`

## Docker-Machine

### Swarm

#### Create
`docker-machine -D rm $HOSTNAME`
`docker-machine -D create -d none --url "tcp://$HOSTNAME:2376" --swarm --swarm-master $HOSTNAME`

#### Env
`eval $(docker-machine env --swarm '$HOSTNAME')`
