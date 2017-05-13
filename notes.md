#### Running a Container
```bash
    docker container run <image_name>:<image_version>
```
for example for a *bare minimum OS + the Apache webserver* type
```bash
    docker container run httpd:2.4
```
Ports mapping. To be able to access http://localhost:80/index.html add port mapping using `-p` flag with some port numbers.
The first number is the port on the host we want to open up, the second is the port in the container we want to map it to.
```bash
    docker container run -p 80:80 httpd:2.4
```
#### Accessing a Container
To list running containers
```bash
    docker container ls
```
To run a command against a running container type
```bash
    docker container exec <container_name> <command>
```
for example
```bash
    docker container exec elegant_noether du -mh
```
##### Attaching a shell to a Container

To attach a standard bash shell the `-i` and `-t` flags can be passed to keep an interactive shell open
```bash
    docker container exec -it elegant_noether /bin/bash
```
##### Installing things in containers
Attach a shell and install `fortunes` package
```bash
    docker container exec -it elegant_noether /bin/bash
    apt-get install -y fortunes
```
Run 
```bash
    /usr/games/fortune
```
to see a random fortune displayed.

##### Update the ENV in a Container
To access `fortune` game without typing every time `/usr/games/fortune` update the PATH environment. After the shell attachment type
```bash
    PATH=$PATH:/usr/games/
    export PATH
    fortune
```

