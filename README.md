## Running multiple Docker Daemons in the same machine

We seperate the number of Docker daemons in the machine
docker : the default installation
docker-apps : the isolated docker installation for applications

### Goal
The main goal is to have separate docker daemons running on the same machine isolated.
Our use case was the jenkins server. I used to run my jenkins server in a docker container and I wanted to isolate the docker that uses jenkins to launch containers.

### Procedure
1. Create the service file for the daemon
Edit appropriately docker-apps.service file and place it in ```/etc/systemd/system/``` directory
``` bash
sudo cp ./docker-apps.service /etc/systemd/system/docker-apps.service
```
2. Create the socket file
``` bash
sudo cp ./docker-apps.socket /etc/systemd/system/docker-apps.socket
```
3. Create the new daemons data-root directory
``` bash
sudo mkdir /var/lib/docker-apps
```
4. Place the configuration file in ```/etc/docker/```
```bash
sudo cp ./docker-daemon-apps.json /etc/docker/docker-apps.json
```
5. Enable new service
``` bash
sudo systemctl enable docker-apps.service
sudo systemctl enable docker-apps.socket
```
6. Run new service
``` bash
sudo systemctl start docker-apps.socket
sudo systemctl start docker-apps.service
```

### Contributors
* Antonios Inglezakis (@antIggl)
