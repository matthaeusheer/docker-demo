# Task 1 - Getting Familiar and Docker Basics

This first task's goal is to interact with the docker CLI and understand how to manage images and containers und your system.

## 0) Prune your system to start with a clean environment (no images, containers, volumes...)
Run `docker system prune -a` and accept with `y`

## 1) Run containers, check for images and containers on your system

**Start a container of type "hello-world"** (see https://hub.docker.com/_/hello-world)

- Make sure to read the output and understand what it's saying.
<details>
  <summary>Solution</summary>

```
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete
Digest: sha256:37a0b92b08d4919615c3ee023f7ddb068d12b8387475d64c622ac30f45c29c51
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```
</details>

**Run the command again.**
- What happens now? Why is it faster?
- Inspect the images present on your local system, how many are there?
- Check the created stamp and compare it with the respective one on Docker Hub. Look around on Docker Hub to get familiar with it.
- Click on the _linux_ tag on Docker Hub (in the Description section of the image) and inspect the Dockerfile which creates this image. What is it doing?

<details>
  <summary>Solution</summary>

```
$ docker images ls
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
hello-world   latest    feb5d9fea6a5   6 weeks ago   13.3kB
```
or with a shortcut
```
$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
hello-world   latest    feb5d9fea6a5   6 weeks ago   13.3kB
```
</details>

**Inspect your system-wide docker information / configuration.**
- Where is the data docker created stored? 
- How many images and containers are currently stored on the system?
<details>
  <summary>Solution</summary>

```
$ docker info
...
```
</details>

**List the containers on your system**

- What is the basic command to list the containers showing? 
- Why are there no containers listed and how can I see them?
- What are the possible states a container can be in (google...)?
<details>
  <summary>Solution</summary>

```
$ docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
or with a shortcut
```
$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

to list excited containers as well: 
```
$ docker ps -a
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
CONTAINER ID   IMAGE         COMMAND    CREATED              STATUS                          PORTS     NAMES
add3bc705fbe   hello-world   "/hello"   About a minute ago   Exited (0) About a minute ago             wizardly_sutherland
d6780e6c8d1d   hello-world   "/hello"   About a minute ago   Exited (0) About a minute ago             magical_black
```
</details>

##2) A real-world scenario using Jenkins

**Fire up an instance of a jenkins image in just a second and play around with it**
```
docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins
```

- Which tag has been used (note: we did not specify any tag in the command above)
- What are the -p options for? Hint: `docker run --help` and https://docs.docker.com/config/containers/container-networking/ (section published ports)
- Check the ENTRYPOINT line in the respective Dockerfile (check on Docker Hub with the respective tag), what is being done when the container starts up?
- When we start a container like this we are in "attached" mode thus the container is attached to our shell and exits when we press Ctrl+C. Stop and start the _same_ container in detached mode again. Be careful not to start a _new_ container of the same image. What would be the difference?
- What other options do we have to stop a running container when it is in attached (and also detached) mode? Hint: `docker container --help`
- Go to localhost:8080 and go through the setup of Jenkins (install packages and skip adding a user)
- The initial admin password has been written to the logs of the running container. How can you get the logs when you are in detached mode? Get the password and enter it in the web UI. Hint: `docker logs --help`

**Entering a running container**  
Run
```
docker exec -it <the_name_of_your_running_jenkins_container> /bin/bash
```
- Try to understand this command, what is it doing?
- The logs of the started jenkins script say the content is written in `/var/jenkins_home/secrets`, try to print out the content of this file (within the docker container).

Note that you can easily enter containers and to whatever you want in there as if you were SSH'ing into a VM.

**Removing containers and images**  
- Read https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/ and clean up your system accordingly.


##