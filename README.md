# How to use Docker? 🐳🚀

## 🌟 Description 🌟

- This project is designed to teach you how to Docker, a powerful tool for creating, deploying, and managing containerized applications.

- Through examples and detailed explanations, you will learn how to:

  - build images
  - manage containers
  - optimize your development workflows.

- Get ready to learn about Docker! 🐳🚀

## 📋 Index 📚

### 01 - Intro 📖

- [05 - Qué es Docker 🐳](#05---qué-es-docker-🐳)
- [09 - Proceso de desarrollo con Docker 🔄](#09---proceso-de-desarrollo-con-docker-🔄)

### 02 - Build Images 🏗️

- [02 - Imagen vs contenedor 🖼️](#02---imagen-vs-contenedor-🖼️)
  - [Abstraction 🧩](#abstraction-🧩)
  - [Image vs container 🛠️](#image-vs-container-🛠️)
- [04 - Dockerfile 📜](#04---dockerfile-📜)
- [05 - Select one image / run one container 🖼️➡️📦](#05---select-one-image--run-one-container-🖼️➡️📦)
- [06 - Copy file into the container 📂➡️📦](#06---copy-file-into-the-container-📂➡️📦)
- [07 - Ignore file 🚫📂](#07---ignore-file-🚫📂)
- [08 - Run commands 🏃‍♂️💻](#08---run-commands-🏃‍♂️💻)
- [09 - Accelerate images ⚡](#09---accelerate-images-⚡)
- [10 - Environment variables 🌍🔧](#10---environment-variables-🌍🔧)
- [11 - Commands CMD 🖥️](#11---commands-cmd-🖥️)
  - [RUN vs CMD ⚔️](#run-vs-cmd-⚔️)
  - [Entrypoint 🚪](#entrypoint-🚪)
- [12 - Ports 🌐](#12---ports-🌐)
- [13 - Users 👤](#13---users-👤)
  - [Create users and groups 👥](#create-users-and-groups-👥)
  - [Add the command in Dockerfile 📝](#add-the-command-in-dockerfile-📝)
- [14 - Delete images 🗑️](#14---delete-images-🗑️)
- [15 - Tags 🏷️](#15---tags-🏷️)

### 03 - Containers 📦

- [02 - Start Containers 🚀](#02---start-containers-🚀)
  - [Create one container 🆕📦](#create-one-container-🆕📦)
  - [Create one container setting up a name 🏷️📦](#create-one-container-setting-up-a-name-🏷️📦)
  - [Start a container ▶️📦](#start-a-container-▶️📦)
  - [Docker run && Docker stop 🏃‍♂️⏹️](#docker-run--docker-stop-🏃‍♂️⏹️)
- [03 - Logs 📜](#03---logs-📜)
  - [Logs -f 🔍](#logs--f-🔍)
  - [Logs -n 🔢](#logs--n-🔢)
  - [Logs -t 🕒](#logs--t-🕒)
- [04 - Ports 🌐](#04---ports-🌐)
- [05 - Start vs Run ⚔️](#05---start-vs-run-⚔️)
- [06 - Delete containers 🗑️📦](#06---delete-containers-🗑️📦)
- [07 - Execute commands 🏃‍♂️💻](#07---execute-commands-🏃‍♂️💻)
  - [In mode interactive 🖱️](#in-mode-interactive-🖱️)
  - [Only execute one command 🛠️](#only-execute-one-command-🛠️)

### 04 - Multiple Containers 🤝

- [02 - Clean all 🧹](#02---clean-all-🧹)
- [04 - File docker-compose.yml 📜](#04---file-docker-compose-yml-📜)
- [05 - Management the images 🛠️](#05---management-the-images-🛠️)
  - [Create 🆕](#create-🆕)
  - [Read 📖](#read-📖)
  - [Update 🔄](#update-🔄)
  - [Delete 🗑️](#delete-🗑️)
- [06 - Logs 📜](#06---logs-📜)
- [07 - Networks 🌐](#07---networks-🌐)
  - [Kinds of networks 🌉](#kinds-of-networks-🌉)
  - [DNS 🌐🔗](#dns-🌐🔗)
- [08 - Independent Containers 🛠️](#08---independent-containers-🛠️)

# 01 - Intro 📖

## **05 - Qué es Docker 🐳**

- Docker, contruye, ejecuta y despliega
- Pueden generar paquetes de nuestra app
  - Si neceitamos versiones especificas de depencencias Docker se encarga de empaquetar estas versiones.
  - Se pasa esta `configuracíon` a producción y funcionará igual
- Podemos tener versiones diferentes de las dependencias
  - cada paquete puede tener versiones especificas del sofware que la app desarrollada este utilizando

## **09 - Proceso de desarrollo con Docker 🔄**

- `Contenedores` son → `Procesos`
  - Los `Procesos` tienen su propio sistema de archivos
  - El sistema de archivos los provee una `Imagen`
  - Una `Imagen` es la apliacación
- La `Imagen` se puede publicar en `Docker Hub`
  - `Docker Hub` es como GitHub, puede almacenar `Imagenes`
  - Puede ser descargado por nuestro ambiente de `producción/qa`

# 02 - Build images 🏗️

## **02 - Imagen vs contenedor 🖼️**

### Abstraction 🧩

- The `application` contains the
  - code
  - and the `build` of the code
- The `proces/deamon` is the
  - representation of one `instance` of the `application`
  - One tab of the Chrome could represent one `process`

![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image.png)

### Image vs container 🛠️

- one `image` contains the signature to run one `container`
- one `container` borns from one `image`
- The `ContainerA` doesn't affect `CotainerB` although both had been born from the same `image`.

![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%201.png)

## 04 - Dockerfile 📜

```docker
# FROM          set the specific base image
# WORKDIR       set the working directory
# COPY          copy files from host to container
# ADD           add files from host to container
# RUN           execute commands in the container
# ENV           set environment variables
# EXPOSE        expose a port of the app
# USER          set the user to run the container, it's to roles and permissions
# CMD           set the command to run when the container starts
# ENTRYPOINT    set the command to run when the container starts
```

## 05 - Select one image / run one container 🖼️➡️📦

```docker
# Dockerfile

FROM node:20.5.0-alpine3.18
```

```bash
$ sudo docker build -t first-docker-app-react .
[sudo] password for jcarlos:
[+] Building 8.5s (5/5) FINISHED

$ sudo docker run -it first-docker-app-react sh
/ # ls
bin    etc    lib    mnt    proc   run    srv    tmp    var
dev    home   media  opt    root   sbin   sys    usr
/ # node -v
v20.5.0
/ #
```

## 06 - Copy file into the container 📂➡️📦

- add the next lines to add file into the container

```docker
FROM node:20.5.0-alpine3.18

WORKDIR /app/

## --- all these works fine ---
# COPY pakcage.json package-lock.json /app/
# COPY pakcage*.json /app/
# COPY . /app/
# COPY ["date from back.json"] /app/
COPY . .

## --- all these works fine ---
## just use this when your files are in one url or .zip
# ADD www.my_website.com .
# ADD myZip.zim .
```

- now you see the file of the proyect into the container

```bash
$ sudo docker build -t first-docker-app-react .
[+] Building 3.2s (8/8) FINISHED                                                          docker:default
 => [internal] load build definition from Dockerfile                                                0.0s
 => => transferring dockerfile: 995B                                                                0.0s
 => [internal] load metadata for docker.io/library/node:20.5.0-alpine3.18                           0.8s
 => [internal] load .dockerignore                                                                   0.0s
 => => transferring context: 2B                                                                     0.0s
 => CACHED [1/3] FROM docker.io/library/node:20.5.0-alpine3.18@sha256:efcfc9e818c3abe166cfcced1c96  0.0s
 => [internal] load build context                                                                   0.7s
 => => transferring context: 54.95MB                                                                0.7s
 => [2/3] WORKDIR /app/                                                                             0.0s
 => [3/3] COPY . .                                                                                  0.9s
 => exporting to image                                                                              0.7s
 => => exporting layers                                                                             0.6s
 => => writing image sha256:5cd2e87c215f79735f0641f4cca30d18bdd990537c11f447d784f24ac277f712        0.0s
 => => naming to docker.io/library/first-docker-app-react                                           0.0s

$ sudo docker run -it first-docker-app-react sh
/app # ls
Appdeejemplo-230822-121629.zip  node_modules                    src
Dockerfile                      package-lock.json               terminal.sh
README.md                       package.json                    vite.config.js
index.html                      public
/app #
```

## 07 - Ignore file 🚫📂

- the weight of the container is smaller
- the container will be faster
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%202.png)
- Build the container again
- Now you don’t see the folder `/node_modules`
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%203.png)

## 08 - Run commands 🏃‍♂️💻

- you need to add this
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%204.png)
- This is the url to watch what command you could use
  - [https://wiki.alpinelinux.org/wiki/Alpine_Package_Keeper](https://wiki.alpinelinux.org/wiki/Alpine_Package_Keeper)
- The command was execurted and the `/node_modules` was added
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%205.png)

## 09 - Accelerate images ⚡

- With the command we can watch the steps that the container follows with each size.
  ```bash
  sudo docker history first-docker-app-react
  ```
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%206.png)
- We need to change the order of the commands in `Dockerfile`
  - With theses changes, the next rebuilds take less time because
    - Only the files of the proyect were updated
    - When Docker detects one change in one of the steps, the next steps will be rebuilded, so it will take more time.
    - With this strategy only the last step will detect change in the files in the project, so this will be the only one that will be rebuilt
      ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%207.png)
- When we run this command twice, we can see that the time was reduced.
  ```bash
  sudo docker build -t first-docker-app-react .
  ```
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%208.png)

## 10 - Environment variables 🌍🔧

- add the variables
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%209.png)
- Execute the next commands
  ```bash
  $ sudo docker build -t first-docker-app-react .
  $ sudo docker run -it first-docker-app-react sh
  /app # printenv
  ```
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2010.png)

## 11 - Commands CMD 🖥️

- Execute the next comands
  - `sudo docker ps` to see the current running containers
  - `sudo docker stop e30` to stop one container, we need the first three chars od the `ID`
  ```bash
  $ sudo docker run first-docker-app-react npm run dev
  $ sudo docker ps
  $ sudo docker stop e30
  $ sudo docker ps
  ```
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2011.png)

### RUN vs CMD ⚔️

- RUN runs when the container is being created.
- CDM runs after the container was setted up.

### Entrypoint 🚪

![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2012.png)

## 12 - Ports 🌐

![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2013.png)

## 13 - Users 👤

- check what user is running in the container
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2014.png)

### Create users and groups 👥

1.  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2015.png)

2.  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2016.png)

### Add the command in Dockerfile 📝

![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2017.png)

- Run the commands
  ```bash
  $ sudo docker build -t first-docker-app-react .
  $ sudo docker run -it first-docker-app-react sh
  whoami
  ```
- now we change the user
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2018.png)
- But the project still belongs to the root user
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2019.png)
- To fix that we need to move the commands to create user and group at the top
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2020.png)
- Also, we need to add `—chown:react` to change for a moment the group and the permissions of the user
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2021.png)
- If you have some error with the permissions, add these lines
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2022.png)
- Run these commands
  ```bash
  $ sudo docker build -t first-docker-app-react .
  $ sudo docker run -it first-docker-app-react sh
  $ cd ..
  $ ls -all
  ```
  - Now the folder app belogs to the user `user01`
    ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2023.png)

## 14 - Delete images 🗑️

```bash
$ sudo docker ps                    # list the current running containers
$ sudo docker ps -a                 # list all containers
$ sudo docker container prune       # list all containers that they aren't running

$ sudo docker images                # list all images
$ sudo docker image prune           # delete all images that they don't have an container locally
$ sudo docker image rm first-docker-app-react # delete one image using the current name
$ sudo docker image rm 74c          # delete one image using the image id
```

## 15 - Tags 🏷️

```bash
$ sudo docker image rm app-react:2
$ sudo docker images
$ sudo docker build -t app-react:2 .
$ sudo docker images
$ sudo docker images
```

- Create a container without tag and tag
  ```bash
  $ sudo docker build -t app-react .
  $ sudo docker build -t app-react:1.0.0 .
  $ sudo docker images
  ```
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2024.png)
- remove a container with tag
  ```bash
  $ sudo docker image remove app-react:1.0.0
  $ sudo docker images
  ```
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2025.png)
- modify tags
  ```bash
  $ sudo docker tag app-react:1 app-react:2
  $ sudo docker images
  ```
  ![image.png](02%20-%20Build%20images%201e68a69dcec780b182a7dcd4c9eabe3e/image%2026.png)

# 03 - Containers 📦

## 02 - Start Containers 🚀

### Create one container 🆕📦

- This command will create one contianer from `app-react` with the `tag`
- Docker gives autotically one name

```bash
sudo docker create app-react:2
```

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image.png)

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%201.png)

### Create one container setting up a name 🏷️📦

```bash
$ sudo docker create --name pepe01 app-react:2
$ sudo docker ps -a
```

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%202.png)

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%203.png)

### Start a container ▶️📦

```bash
$ sudo docker start pepe01
$ sudo docker ps
```

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%204.png)

### Docker run && Docker stop 🏃‍♂️⏹️

```bash
$ sudo docker run -d --name pepe-run app-react:2
$ sudo docker stop cac
$ sudo docker ps -a
```

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%205.png)

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%206.png)

## 03 - Logs 📜

```bash
$ sudo docker images
$ sudo docker run -d --name pepe03 app-react:2
$ sudo docker ps

$ sudo docker logs pepe03
$ sudo docker logs -f pepe03
$ sudo docker logs -n 5 pepe03
$ sudo docker logs -t -n 10 pepe03
```

### Create contianers

```bash
$ sudo docker images
$ sudo docker run -d --name pepe03 app-react:2
$ sudo docker ps
```

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%207.png)

### logs -f

- Follow the logs of the container

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%208.png)

### logs -n

- show the last `n` lines of the contianer

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%209.png)

### logs -t

- show the timestamp

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%2010.png)

## **04 - Ports 🌐**

- Add the flag `-p 5173:5173`

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%2011.png)

## 05 - Start vs Run ⚔️

- `run` use many commands like
  - pull && start
  - also, it creates new container (instance of the image)
- `start` only has the task to setting up one container that it has the state stop
  - this command not create a new container

## **06 - Delete containers 🗑️📦**

- `sudo docker ps -a` to list all containers
- `sudo docker container rm -f 38b8` to delete one contianer that it is running
- `sudo docker container rm c18` to delete con container tha it is stoped

```bash
$ sudo docker ps -a
$ sudo docker container rm -f 38b8
$ sudo docker container rm c18
```

## 07 - Execute commands 🏃‍♂️💻

```bash
$ sudo docker run -d -p 80:5173 --name pepe-run app-react:3
$ sudo docker exec -it pepe-run sh
$ sudo docker exec pepe-run ls
```

### in mode interactive 🖱️

- you need to pass the flag `-it` interactive
- run the command `ls` and `exit`

```bash
$ sudo docker exec -it pepe-run sh
```

![image.png](03%20-%20Containers%201e88a69dcec7800eb40ee1dc03c66a44/image%2012.png)

### only execute one command 🛠️

- You don’t need to send the flag `-it`
- only if you want to send a command

```bash
$ sudo docker exec pepe-run ls
```

# 04 - Multiple Containers 🤝

## 02 - Clean all 🧹

- clean containers
  ```bash
  $ sudo docker container ls -aq
  $ sudo docker container rm -f $(sudo docker container ls -aq)
  $ sudo docker ps -a
  ```
- Clean images
  ```bash
  $ sudo docker image ls -q
  $ sudo docker image rm $(sudo docker image ls -q)
  $ sudo docker image ls -q
  ```

## **04 - File docker-compose.yml 📜**

- The `version` is only informatvie
- The section `services` is where you specify all the applications that they have communication between them.
  - In the example you have 3 applacations: `app`, `api`, `db`
  - The `build` you need to specify what `image` the compose should take to create the `network`
  - The `ports` is where you make it free to be taken by one application
    - The application/service uses `port 5173,` but in order to access it, your computer uses `port 80` so you can access the application/service.
    - You can access it via `localhost:80`, which will connect to the application/service via `port 5173`.
  - The `enviroments` you could use the name of the services to comple the URL
    - The service api needs the service db to it could run.
    - You need to specify next two things
      ```yaml
      environment:
      	DB_URL: mongodb://db/gamify
      depends_on:
        - db
      ```
  - In the case of web app & backend app, theses hava their own `Dockefile`
    - But, the service db doesn’t have one, so in this case you need to specify the db to works.
      ```yaml
      db:
        image: mongo:5.0.19-focal
        ports:
          - 27017:27017
        volumes:
          - gamify:/data/db
      ```

```yaml
version: "3.8"

services:
  app:
    build: ./frontend
    ports:
      - 80:5173
    volumes:
      - ./frontend/src:/app/src
    environment:
      VITE_API_URL: http://localhost:3000
  api:
    build: ./backend
    ports:
      - 3000:3000
    volumes:
      - ./backend/app:/app/app
    environment:
      DB_URL: mongodb://db/gamify
    depends_on:
      - db
  api-tests:
    image: holamundo-api
    environment:
      DB_URL: mongodb://db/gamifytest
    volumes:
      - ./backend/app:/app/app
      - ./backend/tests:/app/tests
    depends_on:
      - db
    command: npm test
  db:
    image: mongo:5.0.19-focal
    ports:
      - 27017:27017
    volumes:
      - gamify:/data/db

volumes:
  gamify:
```

## 05 - Management the images 🛠️

### Create 🆕

- build: Build or rebuild services
- up: Create and start containers
- create: Creates containers for a service
- run: Run a one-off command on a service
- commit: Create a new image from a service container's changes
- publish: Publish compose application

### Read 📖

- logs: View output from containers
- ps: List containers
- version: Show the Docker Compose version information
- config: Parse, resolve and render compose file in canonical format
- images: List images used by the created containers
- ls: List running compose projects
- stats: Display a live stream of container(s) resource usage statistics
- events: Receive real time events from containers
- port: Print the public port for a port binding
- top: Display the running processes

### Update 🔄

- exec: Execute a command in a running container
- restart: Restart service containers
- start: Start services
- attach: Attach local standard input, output, and error streams to a service's running container
- scale: Scale services
- unpause: Unpause services
- watch: Watch build context for service and rebuild/refresh containers when files are updated

### Delete 🗑️

- down: Stop and remove containers, networks
- stop: Stop services
- kill: Force stop service containers
- rm: Removes stopped service containers
- pause: Pause services
- wait: Block until containers of all (or specified) services stop.

## 06 - Log

- list all logs
  ```bash
  docker compose logs
  ```
- options
  ```bash
  docker compose logs --help
  ```
  ```yaml
  **-f, --follow          Follow log output
  -n, --tail string     Number of lines to show from the end of the logs for each container (default "all")
  -t, --timestamps      Show timestamps
  --since string        Show logs since timestamp (e.g. 2013-01-02T13:23:37Z) or relative (e.g. 42m for 42 minutes)
  --until string        Show logs before a timestamp (e.g. 2013-01-02T13:23:37Z) or relative (e.g. 42m for 42 minutes)
  --no-color            Produce monochrome output
  --no-log-prefix       Don't print prefix in logs
  --index int           Index of the container if service has multiple replicas
  --dry-run             Execute command in dry run mode**
  ```

## **07 - Networks 🌐**

### Kinds of networks 🌉

- list the networks used by Docker
  ```bash
  docker networks ls
  ```
  ![image.png](04%20-%20Multiple%20Containers%201e88a69dcec780dab5fed9bfbbaf55ed/image.png)

1. **Bridge Network**
   1. Default network for standalone containers.
   2. Containers on the same bridge network can communicate with each other.
2. **Host Network**
   1. Removes network isolation between the container and the Docker host.
   2. The container shares the host's network stack.
3. **Overlay Network**
   1. Used for multi-host container communication.
   2. Enables communication between containers across different Docker hosts.

### DNS 🌐🔗

- Docker uses one `DNS server`
- Each container has one `DNS resolver`
- When one service/container wants to connect with another servicer/container; Its `DNS resolver` will request the `IP` to the service `DNS of docker`, this has the responsibility to responding the `IP` according with the name of the service/container.
  - the service/container `app` needs to connect with the service/container `api`
  - the service/container \*\*\*\*`api` needs to connect with the service/container `db`
    ![image.png](04%20-%20Multiple%20Containers%201e88a69dcec780dab5fed9bfbbaf55ed/image%201.png)

## 08 - Independent Containers 🛠️

- When you need that one `service` must setting up first before another `service`. You could use the property `depends on` and pass the name of the service that you need.
  ![image.png](04%20-%20Multiple%20Containers%201e88a69dcec780dab5fed9bfbbaf55ed/image%202.png)
- so, docker is gonna wait to setting up the service `db` before the `api`
