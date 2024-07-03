# Docker-ractice


docker version
docker --version
docker info



rpm -qi docker-ce <-- to check docker software installed or not 
docker images  <-- to list all existed images in our local docker registry


----------------------------------------------------------------------------


Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image  <-- Ok 
  exec        Execute a command in a running container
  ps          List containers  <-- Ok
  build       Build an image from a Dockerfile
  pull        Download an image from a registry  <--Ok
  push        Upload an image to a registry <-- Ok
  images      List images <-- Ok
  login       Log in to a registry <-- Ok
  logout      Log out from a registry <-- Ok
  search      Search Docker Hub for images <-- Ok
  version     Show the Docker version information <-- Ok 
  info        Display system-wide information <-- Ok

Management Commands:
  builder     Manage builds
  buildx*     Docker Buildx
  compose*    Docker Compose
  container   Manage containers
  context     Manage contexts
  image       Manage images
  manifest    Manage Docker image manifests and manifest lists
  network     Manage networks
  plugin      Manage plugins
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

Swarm Commands:
  swarm       Manage Swarm

Commands:
  attach      Attach local standard input, output, and error streams to a running container  <-- Ok
  commit      Create a new image from a containers changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a containers filesystem
  events      Get real time events from the server
  export      Export a containers filesystem as a tar archive
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers  <-- OK
  load        Load an image from a tar archive or STDIN
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers  <-- Ok
  port        List port mappings or a specific mapping for the container
  rename      Rename a container <-- OK
  restart     Restart one or more containers  <-- OK
  rm          Remove one or more containers <-- OK
  rmi         Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  start       Start one or more stopped containers  <-- OK
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers  <-- OK
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE  <-- Ok
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers <-- OK
  update      Update configuration of one or more containers
  wait        Block until one or more containers stop, then print their exit codes




----------------------------------------------------------------------------















 Example:

	[root@docker ~]# docker images
	REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
		
	[root@docker ~]#



docker search <-- this command used for to search for the desired images in docker-hub.

Syntax:

   docker search image-name 

 Example:

   [root@docker ~]# docker search hello-world
	NAME                                   DESCRIPTION                                     STARS     OFFICIAL
	
	hello-world                            Hello World! (an example of minimal Dockeriz…   2269      [OK]
	rancher/hello-world                    This container image is no longer maintained…   6
	okteto/hello-world                                                                     0
	garystafford/hello-world               Simple hello-world Spring Boot service for t…   0
	wxia6256/hello-world                   hello-world                                     0
	etapau/hello-world                     k8s hello-world app                             0
	ebenjaminv9/hello-world                Hello-world                                     0



docker pull <-- this command used for to get the image from docker hub to local docker registry

Syntax:

 docker pull image-name


 Example:

 [root@docker ~]# docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
c1ec31eb5944: Pull complete
Digest: sha256:94323f3e5e09a8b9515d74337010375a456c909543e1ff1538f5116d38ab3989
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest
[root@docker ~]#


 Output: 
 [root@docker ~]# docker images
	REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
	hello-world   latest    d2c94e258dcb   14 months ago   13.3kB
	[root@docker ~]#




docker ps <-- this command used for to list all running & Paused containers


Example:

  [root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@docker ~]#


docker ps -a <-- this command used for to list all running, Paused  and exite containers

Example: 

[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@docker ~]#



docker run <-- this command used for to create a new container.  

------------------
docker run   Syntax 1:
------------------

docker run -it image-name 

Example:

  docker run -it hello-world     <-- here we are testing is our docker working or not properly


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






  Note:  by the above command container will create and kill/stop itself  after executing above message.


  docker rm <-- this command used for to delete exited container  

  Syntax:

    docker rm container-id/container-name   

 Note:  make sure is the container existed and exited or not!

		Example:

	  [root@docker ~]# docker ps -a
		CONTAINER ID   IMAGE         COMMAND    CREATED         STATUS                     PORTS     NAMES
		d6e742fc0fc1   hello-world   "/hello"   5 minutes ago   Exited (0) 5 minutes ago             keen_aryabhata

		[root@docker ~]# docker rm keen_aryabhata
		keen_aryabhata

		[root@docker ~]# docker ps -a
		CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

		[root@docker ~]#


------------------
docker run   Syntax 2:
------------------

  docker run -it image-name command


 Example:

  docker run -it centos /bin/bash 

  here --> centos is is the one  plain os Image/Template 
  here --> /bin/bash is the shell command 


  note: by -it container will create and cursor moves into container 




 ------------------------
 coker pull example 2:
------------------------

[root@docker ~]# docker pull centos
Using default tag: latest
latest: Pulling from library/centos
a1d0c7532777: Extracting [==================================================>]  83.52MB/83.52MB


final result after pulling

[root@docker ~]# docker pull centos
Using default tag: latest
latest: Pulling from library/centos
a1d0c7532777: Pull complete
Digest: sha256:a27fd8080b517143cbbbab9dfb7c8571c40d67d534bbdee55bd6c473f432b177
Status: Downloaded newer image for centos:latest
docker.io/library/centos:latest
[root@docker ~]#

-----------------------------

[root@docker ~]# docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    d2c94e258dcb   14 months ago   13.3kB
centos        latest    5d0da3dc9764   2 years ago     231MB
[root@docker ~]#




------------------
docker run   Syntax 3:
------------------

 docker run -itd image-name command

 by above command we are creating a container and running in backend/ditach mode 

Example:

		[root@docker ~]# docker images
		REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
		ubuntu        latest    35a88802559d   3 weeks ago     78.1MB
		hello-world   latest    d2c94e258dcb   14 months ago   13.3kB
		centos        latest    5d0da3dc9764   2 years ago     231MB
		
		[root@docker ~]# docker ps -a
		CONTAINER ID   IMAGE     COMMAND       CREATED       STATUS                   PORTS     NAMES
		97755979194c   ubuntu    "/bin/bash"   2 hours ago   Up 2 hours                         hardcore_solomon
		a8470ef660da   ubuntu    "/bin/bash"   2 hours ago   Exited (0) 2 hours ago             upbeat_johnson
		
		[root@docker ~]# docker run -itd centos /bin/bash
		844681b97dee91d976ab67475c372dc8ec5d134d415ab3b8c2d7eded31e847d2
		
		[root@docker ~]# docker ps
		CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
		844681b97dee   centos    "/bin/bash"   4 seconds ago   Up 3 seconds             stoic_ellis
		97755979194c   ubuntu    "/bin/bash"   2 hours ago     Up 2 hours               hardcore_solomon
		
		[root@docker ~]#



------------------
docker run   Syntax 4:
------------------

 docker run -it  --name jenkins image-name command

by above command we can set the custom container name along with in attach mode 

Example:

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
844681b97dee   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             stoic_ellis
97755979194c   ubuntu    "/bin/bash"   2 hours ago     Up 2 hours               hardcore_solomon
[root@docker ~]# docker run -it --name jenkins centos /bin/bash
[root@62572dcb70d1 /]#


------------------
docker run   Syntax 4:
------------------

docker run -itd  --name jenkins image-name command



by the above command we can create a container in ditach mode along with container name 


Example:

	root@docker ~]# docker run -itd --name jenkins-slave centos /bin/bash
	715f1e8e1efc5ee206c4b640e4360e2ad9bfd452f118f26a72bfe1ebef1610ef
	[root@docker ~]# docker ps
	CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
	715f1e8e1efc   centos    "/bin/bash"   7 seconds ago   Up 6 seconds             jenkins-slave
	62572dcb70d1   centos    "/bin/bash"   3 minutes ago   Up 3 minutes             jenkins
	844681b97dee   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             stoic_ellis
	97755979194c   ubuntu    "/bin/bash"   2 hours ago     Up 2 hours               hardcore_solomon
	[root@docker ~]#



------------------------
docker attach:
-----------------------

Syntax:

 docker attach container-id/container-name  <-- by this command we can attach/we can inter into the container by using docker attach command which container running in ditach mode 

 Example:

 root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   6 minutes ago   Up 6 minutes             jenkins
844681b97dee   centos    "/bin/bash"   9 minutes ago   Up 9 minutes             stoic_ellis
97755979194c   ubuntu    "/bin/bash"   2 hours ago     Up 2 hours               hardcore_solomon

[root@docker ~]# docker attach jenkins
[root@62572dcb70d1 /]#


-----------------------
Error on Stopped container

attach on stopped container
----------------------------------

root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                     PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   3 minutes ago    Up 3 minutes                         jenkins-slave
62572dcb70d1   centos    "/bin/bash"   7 minutes ago    Exited (0) 5 seconds ago             jenkins
844681b97dee   centos    "/bin/bash"   11 minutes ago   Up 11 minutes                        stoic_ellis
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                           hardcore_solomon
a8470ef660da   ubuntu    "/bin/bash"   2 hours ago      Exited (0) 2 hours ago               upbeat_johnson

********************************************************
[root@docker ~]# docker attach jenkins
You cannot attach to a stopped container, start it first
[root@docker ~]#
*********************************************************

Proble Solve on above one:

1. start the container first 
2. then apply docker attach container-id/container-name
   
    Example:

    docker start  jenkins

    docker attach jenkins 

 Practical Example:

root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   8 minutes ago    Up 8 minutes              jenkins-slave
844681b97dee   centos    "/bin/bash"   15 minutes ago   Up 15 minutes             stoic_ellis
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                hardcore_solomon


[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                     PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   8 minutes ago    Up 8 minutes                         jenkins-slave
62572dcb70d1   centos    "/bin/bash"   11 minutes ago   Exited (0) 4 minutes ago             jenkins
844681b97dee   centos    "/bin/bash"   15 minutes ago   Up 15 minutes                        stoic_ellis
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                           hardcore_solomon
a8470ef660da   ubuntu    "/bin/bash"   2 hours ago      Exited (0) 2 hours ago               upbeat_johnson

[root@docker ~]# docker start jenkins
jenkins

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   9 minutes ago    Up 9 minutes              jenkins-slave
62572dcb70d1   centos    "/bin/bash"   12 minutes ago   Up 45 seconds             jenkins
844681b97dee   centos    "/bin/bash"   16 minutes ago   Up 16 minutes             stoic_ellis
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                hardcore_solomon

[root@docker ~]# docker attach jenkins
[root@62572dcb70d1 /]#


--------------------------------------
docker rename:

-----------------------------------
by this command we can rename the container 

Syntax:

 docker rename old/existed-container-name new-container-name 

 Example:

root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   12 minutes ago   Up 12 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   15 minutes ago   Up 3 minutes              jenkins
844681b97dee   centos    "/bin/bash"   19 minutes ago   Up 19 minutes             stoic_ellis
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                hardcore_solomon

[root@docker ~]# docker rename stoic_ellis nexusserver

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   12 minutes ago   Up 12 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   15 minutes ago   Up 4 minutes              jenkins
844681b97dee   centos    "/bin/bash"   19 minutes ago   Up 19 minutes             nexusserver
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                hardcore_solomon

[root@docker ~]#

___________________________________________________________________________________________________________________
--------------------------------
delete the running container:
--------------------------------

step 1:
docker stop container-id/container-name
docker rm container-id/container-name

 Example:

root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   14 minutes ago   Up 14 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   17 minutes ago   Up 5 minutes              jenkins
844681b97dee   centos    "/bin/bash"   21 minutes ago   Up 21 minutes             nexusserver
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                hardcore_solomon

[root@docker ~]# docker stop nexusserver
nexusserver

[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                     PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   14 minutes ago   Up 14 minutes                        jenkins-slave
62572dcb70d1   centos    "/bin/bash"   17 minutes ago   Up 6 minutes                         jenkins
844681b97dee   centos    "/bin/bash"   21 minutes ago   Exited (0) 3 seconds ago             nexusserver
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                           hardcore_solomon
a8470ef660da   ubuntu    "/bin/bash"   3 hours ago      Exited (0) 2 hours ago               upbeat_johnson

[root@docker ~]# docker rm nexusserver
nexusserver

[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                   PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   14 minutes ago   Up 14 minutes                      jenkins-slave
62572dcb70d1   centos    "/bin/bash"   18 minutes ago   Up 6 minutes                       jenkins
97755979194c   ubuntu    "/bin/bash"   2 hours ago      Up 2 hours                         hardcore_solomon
a8470ef660da   ubuntu    "/bin/bash"   3 hours ago      Exited (0) 2 hours ago             upbeat_johnson

[root@docker ~]#



--------------------------------
delete the running container:
--------------------------------

step 2:

 Syntax: 
 docker rm -f container-name/container-id

 here -f means forcefully we are deleting the container

 Example:

 [root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   18 minutes ago   Up 18 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   21 minutes ago   Up 9 minutes              jenkins
97755979194c   ubuntu    "/bin/bash"   3 hours ago      Up 3 hours                hardcore_solomon

[root@docker ~]# docker rm -f hardcore_solomon
hardcore_solomon

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   18 minutes ago   Up 18 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   21 minutes ago   Up 10 minutes             jenkins

[root@docker ~]#


-------------------------------------------
docker pause :
-------------------------------------------

by this command we can put the container in Paused state. 

Note: make sure the container is running or not before applying this. if not running the container..! you can't put in Paused state.'

Syntax:

docker pause container-id/container-name


Example:

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   23 minutes ago   Up 23 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   26 minutes ago   Up 15 minutes             jenkins

[root@docker ~]# docker pause jenkins
jenkins

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                   PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   24 minutes ago   Up 24 minutes                      jenkins-slave
62572dcb70d1   centos    "/bin/bash"   27 minutes ago   Up 15 minutes (Paused)             jenkins

[root@docker ~]#

---------------------------------------
docker unpause
---------------------------------------

Syntax:

docker unpause container-id/container-name

by this command we can unpause the paused container

Note: make sure the container in Paused state.

Example:

root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                   PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   25 minutes ago   Up 25 minutes                      jenkins-slave
62572dcb70d1   centos    "/bin/bash"   29 minutes ago   Up 17 minutes (Paused)             jenkins

[root@docker ~]# docker unpause jenkins
jenkins

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   26 minutes ago   Up 26 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   29 minutes ago   Up 17 minutes             jenkins

[root@docker ~]#


---------------------------------
docker kill
---------------------------------

Syntax:

by above command we can kill/stop the container 


Example:

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   28 minutes ago   Up 28 minutes             jenkins-slave
62572dcb70d1   centos    "/bin/bash"   31 minutes ago   Up 19 minutes             jenkins

[root@docker ~]# docker kill jenkins
jenkins

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   29 minutes ago   Up 29 minutes             jenkins-slave

[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                        PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   29 minutes ago   Up 29 minutes                           jenkins-slave
62572dcb70d1   centos    "/bin/bash"   32 minutes ago   Exited (137) 44 seconds ago             jenkins
a8470ef660da   ubuntu    "/bin/bash"   3 hours ago      Exited (0) 3 hours ago                  upbeat_johnson

[root@docker ~]#

---------------------------
docker stop 
---------------------------

by this command we can stop the container which is in running state. 

Syntax:

 docker stop container-id/container-name

 Example:

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   32 minutes ago   Up 32 minutes             jenkins-slave

[root@docker ~]#

[root@docker ~]# docker stop 715f1e8e1efc
715f1e8e1efc

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                       PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   32 minutes ago   Exited (0) 8 seconds ago               jenkins-slave
62572dcb70d1   centos    "/bin/bash"   36 minutes ago   Exited (137) 4 minutes ago             jenkins
a8470ef660da   ubuntu    "/bin/bash"   3 hours ago      Exited (0) 3 hours ago                 upbeat_johnson

[root@docker ~]#



---------------------------
docker login 
--------------------------

docker login

the above command used for to login dockerhub to push the images from our local docker host machine to dockerhub.
Example:

 root@docker ~]# docker login

Log in with your Docker ID or email address to push and pull images from Docker Hub. If you dont have a Docker ID, head over to https://hub.docker.com/ to create one.
You can log in with your password or a Personal Access Token (PAT). Using a limited-scope PAT grants better security and is required for organizations using SSO. Learn more at https://docs.docker.com/go/access-tokens/

Username: thanish
Password: **********
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credential-stores

Login Succeeded

[root@docker ~]#

---------------------------------
docker logout

----------------------

by this command we can logut from the local docker host machine to

command:


  Example:


------------------------------------
docker tag
-----------------------------
by this command we can tag the image with our docker-hub login name

Syntax:

docker tag image-id docker-hub-login-name/image-name:tag-name

Example:

[root@docker ~]# docker images
REPOSITORY             TAG       IMAGE ID       CREATED         SIZE
ubuntu                 latest    35a88802559d   3 weeks ago     78.1MB
hello-world            latest    d2c94e258dcb   14 months ago   13.3kB
centos                 latest    5d0da3dc9764   2 years ago     231MB
thanish/javagitmaven   latest    02999c46111d   3 years ago     665MB
semoss/docker-tomcat   latest    be5f235b4a3d   3 years ago     801MB

[root@docker ~]# docker tag be5f235b4a3d thanish/docker-tomcat:latest

[root@docker ~]# docker images
REPOSITORY              TAG       IMAGE ID       CREATED         SIZE
ubuntu                  latest    35a88802559d   3 weeks ago     78.1MB
hello-world             latest    d2c94e258dcb   14 months ago   13.3kB
centos                  latest    5d0da3dc9764   2 years ago     231MB
thanish/javagitmaven    latest    02999c46111d   3 years ago     665MB
thanish/docker-tomcat   latest    be5f235b4a3d   3 years ago     801MB
semoss/docker-tomcat    latest    be5f235b4a3d   3 years ago     801MB


----------------------------------------------
docker push
---------------------------------------------

by this command we can Upload/push the our local custom image to our docker-hub REPOSITORY

Syntax:

 docker push docker-hub-login-name/image-name:tag-name

Example:
	root@docker ~]# docker push thanish/docker-tomcat:latest
	The push refers to repository [docker.io/thanish/docker-tomcat]
	378c4e693104: Mounted from semoss/docker-tomcat
	ce8168f12337: Mounted from semoss/docker-tomcat
	latest: digest: sha256:ddac7c834697cefc44b4a17a660af53a5c7037da60d609ec94f5b91fb8cb6149 size: 742

	[root@docker ~]#



---------------
docker logout
----------------

root@docker ~]# docker logout
Removing login credentials for https://index.docker.io/v1/
[root@docker ~]#




----------------------------------------

to delete multiple containers at a time 
----------------------------------------

by this command we can delete one or more containers / all containers at a time


Syntax: 1  <-- to delete one or more at a time. 

docker rm container-id container-name container-id .. nth container-id 


               container delete
               /																				\
               /																				\
               /																				\

              docker rm -f container-name container-id container-id   docker rm container-id container-id container-id


 Example 1:

 [root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED             STATUS                        PORTS     NAMES
715f1e8e1efc   centos    "/bin/bash"   About an hour ago   Exited (0) 49 minutes ago               jenkins-slave
62572dcb70d1   centos    "/bin/bash"   About an hour ago   Exited (137) 54 minutes ago             jenkins
a8470ef660da   ubuntu    "/bin/bash"   4 hours ago         Exited (0) 4 hours ago                  upbeat_johnson
[root@docker ~]# docker rm jenkins-slave 62572dcb70d1 upbeat_johnson
jenkins-slave
62572dcb70d1
upbeat_johnson
[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@docker ~]#


Example 2:

root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
4ab45912c0ad   centos    "/bin/bash"   25 seconds ago   Up 23 seconds             vibrant_faraday
75d781ede395   centos    "/bin/bash"   27 seconds ago   Up 26 seconds             objective_kapitsa
f4ef3e1a8163   centos    "/bin/bash"   29 seconds ago   Up 28 seconds             zen_shirley
[root@docker ~]# docker rm -f vibrant_faraday 75d781ede395 f4ef3e1a8163
vibrant_faraday
75d781ede395
f4ef3e1a8163
[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES





--------------------
stop one or more containers / all containers at a time. 

Syntax 1:

root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED              STATUS              PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   About a minute ago   Up About a minute             blissful_hopper
0865044ecf7d   centos    "/bin/bash"   About a minute ago   Up About a minute             mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   About a minute ago   Up About a minute             determined_bose
028c39a483af   centos    "/bin/bash"   About a minute ago   Up About a minute             sweet_lumiere
2d899f944674   centos    "/bin/bash"   About a minute ago   Up About a minute             goofy_tu
ffb32583aad8   centos    "/bin/bash"   About a minute ago   Up About a minute             mystifying_edison
b2215f9367fe   centos    "/bin/bash"   About a minute ago   Up About a minute             lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   About a minute ago   Up About a minute             gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   About a minute ago   Up About a minute             focused_nightingale
f6e3f4835870   centos    "/bin/bash"   About a minute ago   Up About a minute             musing_banzai
ba2971fccc23   centos    "/bin/bash"   About a minute ago   Up About a minute             dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   About a minute ago   Up About a minute             beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   About a minute ago   Up About a minute             romantic_shaw
a74759115cc1   centos    "/bin/bash"   About a minute ago   Up About a minute             sharp_tu
13ee3237b56d   centos    "/bin/bash"   About a minute ago   Up About a minute             mystifying_lamarr
6d34be543dda   centos    "/bin/bash"   About a minute ago   Up About a minute             objective_lalande
5b51854adbca   centos    "/bin/bash"   About a minute ago   Up About a minute             hardcore_pasteur
31c33648b053   centos    "/bin/bash"   About a minute ago   Up About a minute             keen_kare
[root@docker ~]# docker stop blissful_hopper  sweet_lumiere 6d34be543dda 31c33648b053
blissful_hopper
sweet_lumiere
6d34be543dda
31c33648b053
[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
0865044ecf7d   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             determined_bose
2d899f944674   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             goofy_tu
ffb32583aad8   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             mystifying_edison
b2215f9367fe   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             focused_nightingale
f6e3f4835870   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             musing_banzai
ba2971fccc23   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             romantic_shaw
a74759115cc1   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             sharp_tu
13ee3237b56d   centos    "/bin/bash"   2 minutes ago   Up 2 minutes             mystifying_lamarr
5b51854adbca   centos    "/bin/bash"   3 minutes ago   Up 3 minutes             hardcore_pasteur
[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS                     PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   2 minutes ago   Exited (0) 8 seconds ago             blissful_hopper
0865044ecf7d   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         determined_bose
028c39a483af   centos    "/bin/bash"   2 minutes ago   Exited (0) 8 seconds ago             sweet_lumiere
2d899f944674   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         goofy_tu
ffb32583aad8   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         mystifying_edison
b2215f9367fe   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         focused_nightingale
f6e3f4835870   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         musing_banzai
ba2971fccc23   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         romantic_shaw
a74759115cc1   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         sharp_tu
13ee3237b56d   centos    "/bin/bash"   2 minutes ago   Up 2 minutes                         mystifying_lamarr
6d34be543dda   centos    "/bin/bash"   2 minutes ago   Exited (0) 8 seconds ago             objective_lalande
5b51854adbca   centos    "/bin/bash"   3 minutes ago   Up 3 minutes                         hardcore_pasteur
31c33648b053   centos    "/bin/bash"   3 minutes ago   Exited (0) 8 seconds ago             keen_kare
[root@docker ~]#


 Syntax 2:

  to stop all containers at a time.

  Example:


  [root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
0865044ecf7d   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             determined_bose
2d899f944674   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             goofy_tu
ffb32583aad8   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             mystifying_edison
b2215f9367fe   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             focused_nightingale
f6e3f4835870   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             musing_banzai
ba2971fccc23   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             romantic_shaw
a74759115cc1   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             sharp_tu
13ee3237b56d   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             mystifying_lamarr
5b51854adbca   centos    "/bin/bash"   7 minutes ago   Up 7 minutes             hardcore_pasteur
[root@docker ~]# docker stop $(docker ps)
0865044ecf7d
mystifying_lamport
04cd0deb45b8
determined_bose
2d899f944674
goofy_tu
ffb32583aad8
mystifying_edison
b2215f9367fe
lucid_clarke
d5ad1ca73e41
gracious_grothendieck
20fc12288ae7
focused_nightingale
f6e3f4835870
musing_banzai
ba2971fccc23
dazzling_aryabhata
4602d5cb5d98
beautiful_cray
d1b49c509a2f
romantic_shaw
a74759115cc1
sharp_tu
13ee3237b56d
mystifying_lamarr
5b51854adbca
8
hardcore_pasteur

[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS                      PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   7 minutes ago   Exited (0) 5 minutes ago              blissful_hopper
0865044ecf7d   centos    "/bin/bash"   7 minutes ago   Exited (0) 16 seconds ago             mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   7 minutes ago   Exited (0) 16 seconds ago             determined_bose
028c39a483af   centos    "/bin/bash"   7 minutes ago   Exited (0) 5 minutes ago              sweet_lumiere
2d899f944674   centos    "/bin/bash"   7 minutes ago   Exited (0) 16 seconds ago             goofy_tu
ffb32583aad8   centos    "/bin/bash"   7 minutes ago   Exited (0) 16 seconds ago             mystifying_edison
b2215f9367fe   centos    "/bin/bash"   7 minutes ago   Exited (0) 16 seconds ago             lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   7 minutes ago   Exited (0) 16 seconds ago             gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   7 minutes ago   Exited (0) 15 seconds ago             focused_nightingale
f6e3f4835870   centos    "/bin/bash"   7 minutes ago   Exited (0) 13 seconds ago             musing_banzai
ba2971fccc23   centos    "/bin/bash"   7 minutes ago   Exited (0) 13 seconds ago             dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   7 minutes ago   Exited (0) 13 seconds ago             beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   7 minutes ago   Exited (0) 12 seconds ago             romantic_shaw
a74759115cc1   centos    "/bin/bash"   7 minutes ago   Exited (0) 13 seconds ago             sharp_tu
13ee3237b56d   centos    "/bin/bash"   8 minutes ago   Exited (0) 12 seconds ago             mystifying_lamarr
6d34be543dda   centos    "/bin/bash"   8 minutes ago   Exited (0) 5 minutes ago              objective_lalande
5b51854adbca   centos    "/bin/bash"   8 minutes ago   Exited (0) 10 seconds ago             hardcore_pasteur
31c33648b053   centos    "/bin/bash"   8 minutes ago   Exited (0) 5 minutes ago              keen_kare
[root@docker ~]#

----------------------
to start one or more containers / all containers at a time.

Syntax:

docker start container-id container-name container-id.. nth container-id

Example:

root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                     PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   9 minutes ago    Exited (0) 7 minutes ago             blissful_hopper
0865044ecf7d   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             determined_bose
028c39a483af   centos    "/bin/bash"   9 minutes ago    Exited (0) 7 minutes ago             sweet_lumiere
2d899f944674   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             goofy_tu
ffb32583aad8   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             mystifying_edison
b2215f9367fe   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             focused_nightingale
f6e3f4835870   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             musing_banzai
ba2971fccc23   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             romantic_shaw
a74759115cc1   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             sharp_tu
13ee3237b56d   centos    "/bin/bash"   9 minutes ago    Exited (0) 2 minutes ago             mystifying_lamarr
6d34be543dda   centos    "/bin/bash"   9 minutes ago    Exited (0) 7 minutes ago             objective_lalande
5b51854adbca   centos    "/bin/bash"   10 minutes ago   Exited (0) 2 minutes ago             hardcore_pasteur
31c33648b053   centos    "/bin/bash"   10 minutes ago   Exited (0) 7 minutes ago             keen_kare
[root@docker ~]# docker start blissful_hopper beautiful_cray 5b51854adbca 04cd0deb45b8
blissful_hopper
beautiful_cray
5b51854adbca
04cd0deb45b8
[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   9 minutes ago    Up 20 seconds             blissful_hopper
04cd0deb45b8   centos    "/bin/bash"   10 minutes ago   Up 14 seconds             determined_bose
4602d5cb5d98   centos    "/bin/bash"   10 minutes ago   Up 18 seconds             beautiful_cray
5b51854adbca   centos    "/bin/bash"   10 minutes ago   Up 15 seconds             hardcore_pasteur
[root@docker ~]#


 Syntax 2:

  to start all containers at a time:

  docker stsart $(docker ps -a)



[root@docker ~]# docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                     PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   10 minutes ago   Up About a minute                    blissful_hopper
0865044ecf7d   centos    "/bin/bash"   10 minutes ago   Exited (0) 3 minutes ago             mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   10 minutes ago   Up About a minute                    determined_bose
028c39a483af   centos    "/bin/bash"   10 minutes ago   Exited (0) 8 minutes ago             sweet_lumiere
2d899f944674   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             goofy_tu
ffb32583aad8   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             mystifying_edison
b2215f9367fe   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             focused_nightingale
f6e3f4835870   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             musing_banzai
ba2971fccc23   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   11 minutes ago   Up About a minute                    beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             romantic_shaw
a74759115cc1   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             sharp_tu
13ee3237b56d   centos    "/bin/bash"   11 minutes ago   Exited (0) 3 minutes ago             mystifying_lamarr
6d34be543dda   centos    "/bin/bash"   11 minutes ago   Exited (0) 8 minutes ago             objective_lalande
5b51854adbca   centos    "/bin/bash"   11 minutes ago   Up About a minute                    hardcore_pasteur
31c33648b053   centos    "/bin/bash"   11 minutes ago   Exited (0) 8 minutes ago             keen_kare

[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS              PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   10 minutes ago   Up About a minute             blissful_hopper
04cd0deb45b8   centos    "/bin/bash"   10 minutes ago   Up About a minute             determined_bose
4602d5cb5d98   centos    "/bin/bash"   11 minutes ago   Up About a minute             beautiful_cray
5b51854adbca   centos    "/bin/bash"   11 minutes ago   Up About a minute             hardcore_pasteur

[root@docker ~]# docker srart $(docker ps -aq)
docker: 'srart' is not a docker command.
See 'docker --help'

[root@docker ~]# docker start $(docker ps -aq)
8553d43e1997
0865044ecf7d
04cd0deb45b8
028c39a483af
2d899f944674
ffb32583aad8
b2215f9367fe
d5ad1ca73e41
20fc12288ae7
f6e3f4835870
ba2971fccc23
4602d5cb5d98
d1b49c509a2f
a74759115cc1
13ee3237b56d
6d34be543dda
5b51854adbca
31c33648b053
[root@docker ~]# docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
8553d43e1997   centos    "/bin/bash"   12 minutes ago   Up 2 minutes              blissful_hopper
0865044ecf7d   centos    "/bin/bash"   12 minutes ago   Up 40 seconds             mystifying_lamport
04cd0deb45b8   centos    "/bin/bash"   12 minutes ago   Up 2 minutes              determined_bose
028c39a483af   centos    "/bin/bash"   12 minutes ago   Up 39 seconds             sweet_lumiere
2d899f944674   centos    "/bin/bash"   12 minutes ago   Up 36 seconds             goofy_tu
ffb32583aad8   centos    "/bin/bash"   12 minutes ago   Up 35 seconds             mystifying_edison
b2215f9367fe   centos    "/bin/bash"   12 minutes ago   Up 33 seconds             lucid_clarke
d5ad1ca73e41   centos    "/bin/bash"   12 minutes ago   Up 31 seconds             gracious_grothendieck
20fc12288ae7   centos    "/bin/bash"   12 minutes ago   Up 29 seconds             focused_nightingale
f6e3f4835870   centos    "/bin/bash"   12 minutes ago   Up 27 seconds             musing_banzai
ba2971fccc23   centos    "/bin/bash"   12 minutes ago   Up 25 seconds             dazzling_aryabhata
4602d5cb5d98   centos    "/bin/bash"   12 minutes ago   Up 2 minutes              beautiful_cray
d1b49c509a2f   centos    "/bin/bash"   12 minutes ago   Up 24 seconds             romantic_shaw
a74759115cc1   centos    "/bin/bash"   12 minutes ago   Up 22 seconds             sharp_tu
13ee3237b56d   centos    "/bin/bash"   12 minutes ago   Up 20 seconds             mystifying_lamarr
6d34be543dda   centos    "/bin/bash"   12 minutes ago   Up 18 seconds             objective_lalande
5b51854adbca   centos    "/bin/bash"   12 minutes ago   Up 2 minutes              hardcore_pasteur
31c33648b053   centos    "/bin/bash"   12 minutes ago   Up 16 seconds             keen_kare
[root@docker ~]#





----------------------------------------------------------------
docker rm -f $(docker ps)
----------------------------------------------------------------







----------------------------------------
docker rm $(docker ps -a )
------------------------------------------







----------------------------------------
docker rm -f $(docker ps -a )
------------------------------------------


