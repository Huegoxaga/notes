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
  - `microsoft/mssql-server-linux` - This tells Docker which image to use.

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

### Remove Images

- When removing top layer images all related layers will be untagged first. The layers will only be deleted when no top layer images are tagged to it or no existing containers rely on it.
- `docker rm <repoName>:<TagName>`, remove certain image
- `docker rm <repoName>`, remove a certain image
- `docker rm <repoName>@<Digest>`, remove certain image
- `docker rm <ImageID>`, remove certain an image using image ID.
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

### Use Docker Hub Account

- [Go](https://hub.docker.com/) to its website to register an account.
- run `docker login` to enter credentials to login and the access to the images.
- run `docker logout` to logout.
- run `docker search <keyword>` to search images, then use `docker pull` to download.
  - `--filter=stars=5` to return 5 stars result only.
  - Any results do not come with the username is the official image.
- run `docker push username/reponame:tagname` to push a local image to the personal repository in the `Docker Hub` registry.

### Manage Data

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
- It supports comments after `#`

##### Commands

- `FROM`
  - It must be the first command in a `Dockerfile`.
  - It specify the base image for the customized image. Ex, `FROM nginx`
  - `FROM scratch` an empty image for apps that can run on machine by itself.
    - Suitable for apps developed by GOlang.
- `RUN`
  - Can be used to execute CLI commands.
  - Commands followed by it will be run.
  - or append `[filename, param1, param2]` to `RUN` command, then the file will also be executed.
  - To avoid redudent layers, multiple commands should be combined by using `&&` and using one `RUN` command.

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

### Docker Compose

- The official container orchestration tool supported by Docker.
- Uses `YAML` format file(`docker-compose.yml`) to define multiple containers at once and let them work together.
- A service is a container, or multiple container instances that running the same image.
- A project is made of by a series of services, defined in the `docker-compose.yml`.
- It is written in `Python`, uses `Docker API`.
- It supports `Linux`, `macOS`, `Windows 10`.
- `Docker Desktop for Mac/Windows` includes `docker-compose`

### Kubernetes

##### Introduction

- Also known as k8s.
- The open source container orchestration tool developed and supported by Google, donated to Cloud Native Computing Foundation (CNCF).
- Written in Golang.
- Supports managing multiple containers works with cloud platforms and internal data center.

##### Architecture

- A cluster is consisted of one or more master nodes and one or more worker nodes.
  - Multiple master nodes are used to achieve high availability.
  - one cluster can have no more than 5000 nodes, 150,000 pods and 300,000 containers.
- Each node can have multiple pods.
  - There are two types of nodes master nodes and work nodes. master nodes are used to control, monitor worker nodes.
  - A node can be phsical machine or VM or VM Cloud.
  - one node can have no more than 100 pods.
  - A service is set of pods that work together.
    - pods in a service share a single domain name and can be load balanced.
- Each pod can have multiple containers.
  - Each pod will have an unique IP and all containers in the pod shares a single volumn.
  - The volumn can be cloud storage, or network work storage like Network File System.
- A master node has four components
  - API Server - It is uses API transmit cluster info and config in JSON format, it is responsibe for all communications between developer and the cluster. It can be used by two API tool from the client side:
    - Command line tool `kubectl`, which is a Go lang binary.
    - Kubernetes Dashboard
  - Scheduler - schedules pods on nodes and read config files.
    - It will select node for scheduling new pods based on the hardware config info from the config file.
    - It read resource usage data from worker nodes via the API server from ETCD database.
  - Controller Manager - runs controllers,
    - kube-controller-manager - control local machines
      - Ensures nodes are running all the time
      - Ensures the number of pods are the same as
      - controller watch the environment in a certain interval and take acting accordingly.
      - it has the following controller, each of them is a separate process, but compiled into a single binary and run as a single process.
        - Node controller - monitor the nodes health
        - Replication controller(rc or rcs)
          - Auto restart failed containers, nodes based on health check result
          - Replication Controler make sure the number of pods and settings defined in the Manifest file is always satisfied.
        - Endpoints controller - maintain endpoint services
        - Service account and token controllers - maintain account credentials.
    - cloud-controller-manager - control cloud machines
      - Node Controller - monitor the cloud nodes health
      - Route Controller - setup the cloud nodes routes
      - Service Controller - setup cloud provider load balancers
      - Volume Controller - setup cloud volumes
  - Etcd - open source, distributed key-value database from CoreOS.
    - It is only connected to the API Server
    - Can be a part of master node or configured externally.
    - It has a max size of 1MB.
    - It stores `Secret` data - `Secret` is a k8s object which stores sensitive data like credentials.
    - It stores `Config Maps` data - a K8s objects stores configs.
- A worker node has three components
  - kubelet - connected to the master API Server, reponsible for communication.
    - It is reponsible for keeping pod health, according to the requirement in the `PodSpecs`
    - When pod is unhealthy, it will try to restart or run it on a different node
    - It only manage containers created by k8s
  - kube-proxy - maintain network config & rules and exposes services available to the internet.
    - It watches API server on the master node for instructions.
  - container runtime
    - a software which is reponsible for running containers
    - common container runtime
      - Docker
      - Containerd
      - Cri-o
      - Rktlet
      - Kubernetes CRI(Container Runtime Interface)
- K8s Addons are available for providing dashboard, monitoring, centralized logging, and DNS management.
- Automatic bin packing - auto assign jobs amongst containers based on memory and requirement.
- Rollout happens when new changes are deployed, rollbacks can be used to revert changes.
  - This is auto handled by k8s with no downtime.
  - When errors are detected during rollout, k8s will rollback.
- Horizontal Pod Autoscaler - is used to add or remove pods based on CPU utilization by changing setting in the Replication Controller. It can also auto scales by using commands or dashboard.
- K8s can also run jobs, which is controlled and scheduled by the Job Controller
  - each job can be run on one or more pods as required and do auto scaling.
  - when the job is complete all pods will be shutdown

##### Installation

- Online Kubernetes Labs - Web based console for learning k8s
  - [Kubernetes Playground](https://www.katacoda.com/courses/kubernetes/playground)
  - [Play with K8s](https://labs.play-with-k8s.com)
  - [Play with Kubernetes Classroom](https://training.play-with-kubernetes.com)
- Installation Tools - Minimun installation that run a single node cluster inside a VM on the laptops for development
  - [Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/#installation)
  - [Kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
- Cloud based Kubernetes services - Provide setting and let the cloud service setup everything
  - GKE - Google Kubernetes Engine
  - AKS - Azure Kubernentes Service
  - Amazon EKS
