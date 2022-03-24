# Docker

## Introduction

- Developed by Solomon Hykes. It is a private project first, then release on GitHub in March 2013.
- Solomon Hykes is the founder of `dotCloud`, the company renamed as `Docker, Inc.` on Oct 10th, 2013.
- Docker is developed with Google's programming language GO, based on cgroup and namespace of Linux Kernel and AUFS (short for advanced multi-layered unification filesystem) technology.
- It is an operating system level virtualization technology which utilizes a docker engine instead of hypervisor which runs VMs on a hardware level.
- Docker is faster, more portable. It can run thousands of container on a single machine.
- Docker Image is a special, pre-configured file system that contains all the files required for an application. It is immutable.
  - Each App ususlly requires the `root` file system of an entire OS.
  - `Union FS` like `AUFS` is used to separate the app files and OS files of an image to reduce redundancy. So multiple images can share one OS image.
  - All the layers are automatically managed by Docker.
- Each running instance of an image is called a container. Container runs apps on the Host OS directly regardless the type of the Host OS.
  - Container has two layers of storage
    1. It has a realy-only base layer containes files from the image.
    2. It has a storage layer that storage temp files and data stored here will be lost when the instance is deleted or restarted.
  - The best practice is to mount a volumn or directory form the host OS for a persistent storage.
- Docker Registry contains repositories for images.
  - `Docker Hub` is the official Docker Registry.
  - Each repository has differect versions of images for one App.
  - The name of the image is usually `<repoName>:<tagName>`.
  - The tag name is the version for the image. If it is ignored the laster version will be chosen.
  - The `repoName` is usually named as `userName/appName`.
  - An image for Docker Registry Server is available for user to establish private docker registries.
- Docker has a `CE` edition and a `EE` edition.
  - `CE` is free.
  - `EE` is safer.

## Installation

- [Click here](https://docs.docker.com/install/) to see docs for installing Docker Engine on Linux servers.
- Docker Desktop for Mac
  - [Click](https://download.docker.com/mac/stable/Docker.dmg) to download the latest stable version. Double click to install.
  - Optionally, using `homebrew`, run `brew cask install docker` in the terminal.
- Docker Desktop for Windows,
  - Docker Desktop for Windows needs Windows 10 Pro 64 bit and activates Hyper-V.
  - [Click](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe) to download the latest stable version. Double click to install.

## Usage

### Download Images

- Images will be downloaded layer by layer.
- run `docker pull <repositoryName>:<TagName>`, pulling images from Docker Hub's official library.
- Ex: `docker pull ubuntu:18.04` it is the same as `docker pull library/ubuntu:18.04`
- run `docker pull <userName/repoName>:<TagName>`, pulling from the repo of certain user.
- run `docker pull <Docker Registry PI[:Port]/[UserName]</RepoName>:<TagName>`, pulling from a private registry.

### Check Status

- run `docker image ls` list all top layer images
  - same as, `docker images`.
- run `docker image ls -a` list all images in different layers.
- run `docker image ls <RepoName>` list all top layer images for certain repo.
- run `docker image ls <RepoName>:<TagName>` list certain top layer images.
- run `docker image ls -f since=<RepoName>:<TagName>` list by using filter, show all top layer images after certain one is created.
- run `docker image ls -q` lists all top layer images's Image ID.
- run `docker image ls --digests` lists the images digest which is the full SHA256 Key.
- list with a certain format, [Click](https://docs.docker.com/engine/reference/commandline/images/#format-the-output) to see some examples. [Click](https://gohugo.io/templates/introduction/) to see complete format templates.
- run `docker ps` check the container status.
- run `docker system df` check the docker file size on the Host OS.
- run `docker container ls` check running container info.
- run `docker container ls -a` check all container info including stopped container.
- run `docker volume ls` check all volumns.
- run `docker volume inspect <VolumnName>` on host machine to check detailed info.
- run `docker inspect <ContainerNameorID>` check container detailed info.

### Start a Container

- run `docker run <RepoName>:<TagName> <ContainerCommandPath> <ContainerCommand>`, Run from a new image, execute a command then stop the container.
  - if the image is not found locally, Docker will download one immediately.
  - It will assign a new IP address for the container instance.
- Run an interactive Linux OS

  ```s
  docker run -it --rm \
  ubuntu:18.04 \
  bash
  ```

  - Optionally, run `$ docker run -t -i ubuntu:18.04 /bin/bash`
  - `-it` means open an interactive pseudo terminal.
  - `-t` create a pesudo TTY connection
    - some container needs `-t` to keep running, because their image might have a default command bash, it will exit immediately when running in `-d` mode
  - `--rm` means remove the container upon exiting.
  - Third line is the shell for interaction after the container started.
  - run `exit` to quit the container when done.

- run `docker container start` restart a stopped container.
- run `docker start <containerIDorNames>` start a stopped container.
- run `$ docker run -d <RepoName>:<TagName> <ContainerCommandPath> -c "command enter here"`, run command in background and return the `containerID`. Stop container when done.
  - Ex: `$ docker run -d ubuntu:18.04 /bin/sh -c "while true; do echo hello world; sleep 1; done"`.
  - To get the output, run `docker container logs <containerIDorNames>`.
  - If the container is an interactive terminal `-it`, run `docker attach <containerIDorNames>` to access its terminal. The container will be stopped upon exiting the terminal.
  - If the container is an interactive terminal `-it`, run `$ docker exec -it <containerIDorNames> bash` to access its terminal using bash shell. The container will not be stopped upon exiting the terminal.
- run `docker run -d --name sql_server_demo -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=reallyStrongPwd123' -p 1433:1433 microsoft/mssql-server-linux`
  - `--name sql_server_demo` - Another optional parameter. This parameter allows you to name the container. This can be handy when stopping and starting your container from the Terminal.
  - `-e 'ACCEPT_EULA=Y'` - The Y shows that you agree with the EULA (End User Licence Agreement). This is required in order to have SQL Server for Linux run on your Mac.
  - `-e 'SA_PASSWORD=reallyStrongPwd123'` - Required parameter that sets the sa database password.
  - `-p 1433:1433` - This maps the local port 1433 to port 1433 on the container. This is the default TCP port that SQL Server uses to listen for connections.
    - One can map multiple ports from host to container instance `-p 80:80 -p 1433:1433`
  - `-d` Runs the container in detached mode leaving your current terminal free as well as allowing the container to run in the background.
  - `microsoft/mssql-server-linux` - This tells Docker which image to use.
- optionally, run `docker exec`
- `docker run --rm -it -v $(pwd):/data <ImageName> cp <CopyFileFrom> /data` mount a data volumn to the local directory then copy a from to the volumn from the container.
  - `-v` is used to mount a volumn
- `docker run -d --restart unless-stopped redis` run am image in the background and always start it automatically unless manually stopped

### Stop a Container

- run `docker container stop <containerIDorNames>`, stop a running container.
- In an interactive terminal, enter `exit` or press `Ctrl+D` will stop the running command and stop the container.
- Restart a running container
  - run `docker container restart <containerIDorNames>`, stop the running container and start it again.
- Export / Import container snapshots
  - run snapshotw won't store container's user history and metadata.
  - run `docker export <containerIDorNames>` export the container as `.tar` file.
  - run `cat fileName.tar | docker import - UserName/RepoName:TagName`, import a `.tar` file as a local image.
  - run `docker import http://example.com/exampleimage.tgz username/reponame` Import container zipped file from URL.

### Change Images

- Create a new image from old:
  - run `docker commit -m 'commit messages' <ContainerName> <NewImageName>`
  - Changes made to an old image on a running container can be saved to a new image.
- Tag an Image
  - run `docker tag <IMAGE_ID> <accountname>/<repo>:<tag>`
    - account and repo name should all be lowercase.
- Save image as a tar `docker save -o <path for generated tar file> <image name>`
  - or, `docker save <image name> > <path for generated tar file>`
  - Then, the image can be saved as tar or moved to other OS
- Unpack image tar for use `docker load -i <path to image tar file>`

### Remove Images

- When removing top layer images all related layers will be untagged first. The layers will only be deleted when no top layer images are tagged to it or no existing containers rely on it.
- `docker image rm <repoName>:<TagName>`, remove certain image
- `docker image rm <repoName>`, remove a certain image
- `docker image rm <repoName>@<Digest>`, remove certain image
- `docker image rm <ImageID>`, remove certain an image using image ID.
  - It requires only the first few characters of the image ID, as long as the CLI can find a unique match.
- Combines command to delete a batch of images.
  - `$ docker image rm $(docker image ls -q <RepoName>)` delete all images of certain repo.
  - `$ docker image rm $(docker image ls -q -f after=<RepoName>:<TagName>)` delete all images after the creation of certain repo.
- run `docker image prune`, clear outdated images(dangling images).
  - dangling image is a top layer image that has repo name and tag name as `<none>`.
  - Its name got removed when a new image is released with the same name.
  - They are useless and can be deleted.

### Remove Containers

- run `docker container rm <containerIDorNames>`, remove a stopped container.
- run `docker container -f rm <containerIDorNames>`, send kill signal and remove a running container.
- run `docker container prune` remove all stopped containers.
- run `docker container -v rm <containerIDorNames>`, remove a stopped container along with its attached volumn.

### Clean Up

- run `docker system prune` This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all dangling images
  - all dangling build cache

### Use Docker Hub Account

- [Go](https://hub.docker.com/) to its website to register an account.
- run `docker login` to enter credentials to login and the access to the images.
- run `docker logout` to logout.
- run `docker search <keyword>` to search images, then use `docker pull` to download.
  - `--filter=stars=5` to return 5 stars result only.
  - Any results do not come with the username is the official image.
- run `docker push <username>/<reponame>:<tagname>` to push a local image to the personal repository in the `Docker Hub` registry.

### Manage Data

- Move file
  - run `docker cp <SourcefilePath> <ContainerName>:<DestinationPath>`
- A Volumn can store data independently, it can be shared or attached to any contianer and remains in the Host OS by default even the container is deleted. Any changes on the volumn will take effect immediately.
- run `docker volume create <VolumnName>` to create a volumn.
- add `--mount source=<VolumnName>,target=<FoldertoMount>` in the `docker run` command to mount one or more volumns on a container.
- run `docker volume rm <VolumnName>` remove a volumn.
- run `docker volume prune` remove volumns that are not attached to any container.
- add `--mount type=bind,source=<HostFolderPath>,target=ContainFolderPath` in the `docker run` command to create a shared folder.
- add `--mount type=bind,source=<HostFolderPath>,target=ContainFolderPath, readonly` in the `docker run` command to create a readonly shared folder.
  - By default, the container have read and write access to the shared folder.
  - Must use absolut path on existing folders.
- add `--mount type=bind,source=<HostSideFilePath>,target=<ContainerFilePath>` in the `docker run` command to establish a shared file.

### Dockerfile

- It is used to define customized images.
- Scripts for defining an image is store in a file called `Dockerfile` without any extension
- It is consisted of a serires of commands that will be executed in order.
  - Each command will compose one layer for the image.
  - The max number of layers is 127.
- It supports new lines with `\`
  - Empty continuation lines will become errors in a future release.
- It supports comments after `#`

#### Commands

- `FROM`
  - It must be the first command in a `Dockerfile`.
  - It specify the base image for the customized image. Ex, `FROM nginx`
  - `FROM scratch` an empty image for apps that can run on machine by itself.
    - Suitable for apps developed by GOlang.
- `RUN`
  - Each `RUN` command create a new image layer
  - Can be used to execute CLI commands.
  - Commands followed by it will be run.
  - or append `[filename, param1, param2]` to `RUN` command, then the file will also be executed.
  - To avoid redudent layers, multiple commands should be combined by using `&&` and using one `RUN` command.
- `CMD` and `CHECKPOINT`
  - Both command will be executed during the `docker run` command after the image is built
  - The recommanded form is to append `["command", "param1", "param2"]` for both `CMD` and `CHECKPOINT`
  - `CMD` can be overridden by appending command after `docker run`
  - `CHECKPOINT` can be overridden by using the `--checkpoint` flag when executing `docker run`
  - Only the last `CMD` or `CHECKPOINT` command in a dockerfile will be executed
  - When both `CHECKPOINT` and `CMD` are in the same dockerfile, `CHECKPOINT` is used to specify the actual command and `CMD` is used to specify the parameter for the command in `CHECKPOINT`
  - Usually, use `CMD [ "bash", "docker/launch.sh" ]`
    - Because only one command will be executed during launch, use bash script to include all the necessary commands inside. For background processes, each line except the last should end with `&` in the bash script
    - When the last service has `&` the container will stop and exit immediately. [Click Here](https://docs.docker.com/config/containers/multi-service_container/) for alternative solutions

##### Build Image

- `docker build -t <repoName>:<TagName> <contextfolderpath>`
  - context folder is the folder that will be uploaded to Docker server for generating image.
  - By default the `Dockerfile` in the context folder will be executed.
  - use `-f <filepath>` to specify the file as the docker file.
  - use `.dockerignore` to specify the files to be ignored for uploading.
  - `docker build <GitHubURL>#:<FolderName>` build from git repo
  - `docker build <TarURL>` download tar as context folder then build.
  - `docker build - < Dockerfile` or `cat Dockerfile | docker build -` build from files using standard input.
  - `docker build - < <filepath>` build from compressed files using standard input.
- `docker build -t <app-name> .` build an image to the local image server from the Dockerfile in the current directory

### Docker Compose

- The official container orchestration tool supported by Docker.
- Uses `YAML` format file(`docker-compose.yml`) to define multiple containers at once and let them work together.
- A service is a container, or multiple container instances that running the same image.
- A project is made of by a series of services, defined in the `docker-compose.yml`.
- It is written in `Python`, uses `Docker API`.
- It supports `Linux`, `macOS`, `Windows 10`.
- `Docker Desktop for Mac/Windows` includes `docker-compose`
