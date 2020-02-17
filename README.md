## Running multiple Docker Daemons in the same machine

We seperate the number of Docker daemons in the machine
docker : the default installation
docker-apps : the isolated docker installation for applications

### Goal
The main goal is to have separate docker daemons running on the same machine isolated.
Our use case was the jenkins server. I used to run my jenkins server in a docker container and I wanted to isolate the docker that uses jenkins to launch containers.

### Procedure
1. Create the service file for the daemon
2. Create the socket file
3. Create the new daemons data-root directory

4. Enable new service
5. Run new service

