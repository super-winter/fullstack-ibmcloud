
# ibmcloudprivate-commerce-docker-swarm
Step by Step to deploy and scale the IBM WebSphere Commerce Container into Docker Swarm IBM Cloud Private

### Welcome to Commerce Docker Swarm for Cloud Private

#### Basic instructions:

:one: Download [Commerce ICP & Swarm docker-compose.yml](https://github.com/imvieira/fullstack-ibmcloud/blob/master/Commerce%20IBM%20Cloud%20Private%20%26%20Docker%20Swarm/docker-compose.yml)

:two: `docker swarm init`

:three: `docker stack deploy -c docker-compose.yml commerce`

#### Run your new load-balanced app

:large_blue_circle: `docker swarm init `

:large_blue_circle: ` docker stack deploy -c docker-compose.yml commerce `

Get the service ID for the one service in our application:

:large_blue_circle: ` docker service ls `

```
ID                  NAME                       MODE                REPLICAS            IMAGE                              PORTS
vdqggnpxbd2f        commerce_customization     replicated          1/1                 redhat_server/commerce:xc-app0     *:9080->9080/tcp, *:9443->9443/tcp
06ytajesxvo3        commerce_db2               replicated          1/1                 redhat_server/commerce:db2         *:50000->50000/tcp
wb6uhont9ned        commerce_storegars         replicated          0/1                 redhat_server/commerce:crs-app0    *:8080->8080/tcp, *:8443->8443/tcp
zpk6axpc6ihb        commerce_transactionsrvr   replicated          0/1                 redhat_server/commerce:ts-app0     *:5080->5080/tcp, *:5443->5443/tcp, *:9043->9043/tcp, *:9060->9060/tcp
g23b1qkjxb7y        commerce_utilscommerce     replicated          1/1                 redhat_server/commerce:ts-utils    
w6dhol7587g4        commerce_webserver         replicated          3/3                 redhat_server/commerce:lbcluster   *:80->80/tcp

```

You can run `curl http://localhost` several times in a row, or go to that URL in your browser and hit refresh a few times.

### Take down the app and the swarm
#### Take the app down with `docker stack rm:`

:large_blue_circle:``` docker stack rm commerce ```

#### Take down the swarm.

:large_blue_circle:``` docker swarm leave --force ```


Some commands to explore at this stage:

- [X] docker stack ls                                            # List stacks or apps
- [X] docker stack deploy -c (composefile) (appname)  # Run the specified Compose file
- [X] docker service ls                 # List running services associated with an app
- [X] docker service ps (service)                  # List tasks associated with an app
- [X] docker inspect (task or container)                   # Inspect task or container
- [X] docker container ls -q                                      # List container IDs
- [X] docker container logs (ContainerID)                        # See Logs
- [X] docker stack rm (appname)                             # Tear down an application
- [X] docker swarm leave --force      # Take down a single node swarm from the manager

![](https://github.com/imvieira/fullstack-ibmcloud/blob/master/Commerce%20IBM%20Cloud%20Private%20&%20Docker%20Swarm/Swarm_Stack_Init.gif?raw=true)
![](https://github.com/imvieira/fullstack-ibmcloud/blob/master/Commerce%20IBM%20Cloud%20Private%20&%20Docker%20Swarm/Commerce_Visist_Count.gif?raw=true)
