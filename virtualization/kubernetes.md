# Kubernetes

## Introduction

* Also known as k8s.
* The open source container orchestration tool developed and supported by Google, donated to Cloud Native Computing Foundation \(CNCF\).
* Written in Golang.
* Supports managing multiple containers works with cloud platforms and internal data center.

## Architecture

* A cluster is consisted of one or more master nodes and one or more worker nodes.
  * Multiple master nodes are used to achieve high availability.
  * one cluster can have no more than 5000 nodes, 150,000 pods and 300,000 containers.
* Each node can have multiple pods.
  * There are two types of nodes master nodes and work nodes. master nodes are used to control, monitor worker nodes.
    * Each node will have an IP address
  * A node can be phsical machine or VM or VM Cloud.
  * one node can have no more than 100 pods.
  * A service is set of pods that work together.
    * pods in a service share a single domain name and can be load balanced.
* Each pod can have one or more containers.
  * Each pod will have an unique IP and all containers in the pod shares a single volumn.
  * The volumn can be cloud storage, or network work storage like Network File System.
* A master node has four components
  * API Server - It is uses API transmit cluster info and config in JSON format, it is responsibe for all communications between developer and the cluster. It can be used by two API tool from the client side:
    * Command line tool `kubectl`, which is a Go lang binary.
    * Kubernetes Dashboard
  * Scheduler - schedules pods on nodes and read config files. It is where the desired state is defines.
    * It will select node for scheduling new pods based on the hardware config info from the config file.
    * It read resource usage data from worker nodes via the API server from ETCD database.
  * Controller Manager - runs controllers. It drives the current state to the desired state.
    * kube-controller-manager - control local machines
      * Ensures nodes are running all the time
      * Ensures the number of pods are the same as
      * controller watch the environment in a certain interval and take acting accordingly.
      * it has the following controller, each of them is a separate process, but compiled into a single binary and run as a single process.
        * Node controller - monitor the nodes health
        * Replication controller\(rc or rcs\)
          * Auto restart failed containers, nodes based on health check result
          * Replication Controler make sure the number of pods and settings defined in the Manifest file is always satisfied.
        * Endpoints controller - maintain endpoint services
        * Service account and token controllers - maintain account credentials.
    * cloud-controller-manager - control cloud machines
      * Node Controller - monitor the cloud nodes health
      * Route Controller - setup the cloud nodes routes
      * Service Controller - setup cloud provider load balancers
      * Volume Controller - setup cloud volumes
  * Etcd - open source, distributed key-value database from CoreOS.
    * It is only connected to the API Server
    * Can be a part of master node or configured externally.
    * It has a max size of 1MB.
    * It stores `Secret` data - `Secret` is a k8s object which stores sensitive data like credentials.
    * It stores `Config Maps` data - a K8s objects stores configs.
* A worker node has three components
  * kubelet - connected to the master API Server, reponsible for communication.
    * It is reponsible for keeping pod health, according to the requirement in the `PodSpecs`
    * When pod is unhealthy, it will try to restart or run it on a different node
    * It only manage containers created by k8s
  * kube-proxy - maintain network config & rules and exposes services available to the end users.
    * It watches API server on the master node for instructions.
  * container runtime
    * a software which is reponsible for running containers
    * common container runtime
      * Docker
      * Containerd
      * Cri-o
      * Rktlet
      * Kubernetes CRI\(Container Runtime Interface\)
* K8s Addons are available for providing dashboard, monitoring, centralized logging, and DNS management.
* Automatic bin packing - auto assign jobs amongst containers based on memory and requirement.
* Rollout happens when new changes are deployed, rollbacks can be used to revert changes.
  * This is auto handled by k8s with no downtime.
  * When errors are detected during rollout, k8s will rollback.
* Horizontal Pod Autoscaler - is used to add or remove pods based on CPU utilization by changing setting in the Replication Controller. It can also auto scales by using commands or dashboard.
* K8s can also run jobs, which is controlled and scheduled by the Job Controller
  * each job can be run on one or more pods as required and do auto scaling.
  * when the job is complete all pods will be shutdown
* Networking
  * The two main types of Kubernetes networking services:
    1. ClusterIP
       * This is the default service type
       * This provides a virtual IP that can only be accessed within the cluster
    2. NodePort
       * Assigns a ClusterIP and a port between 30000-32767
       * These are mapped to the service
  * The definitions of these services reference three different kinds of ports and it is important to understand the differences between them:
    1. Port \(ClusterIP and NodePort service types\)
       * This is the port number that makes the service visible to the rest of the cluster
       * If another service needs to communicate with this service, it would do so with: `[ClusterIP]:[Port]`
    2. TargetPort \(ClusterIP and NodePort service types\)
       * This is the port within the container that the app is actually running on.
       * In the NGINX example, port 80 is where the web server listens for http requests
       * This is the port that the service will forward traffic on
    3. NodePort \(Only NodePort service type\)
       * This is the port which makes the service visible from outside of the cluster
       * This port can be used to access the service externally with `[node's IP]:[nodeport]`

## Installation

* Online Kubernetes Labs - Web based console for learning k8s
  * [Kubernetes Playground](https://www.katacoda.com/courses/kubernetes/playground)
  * [Play with K8s](https://labs.play-with-k8s.com)
  * [Play with Kubernetes Classroom](https://training.play-with-kubernetes.com)
* Installation Tools - Minimun installation that run a single node cluster inside a VM on the laptops for development
  * [Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/#installation)
  * [Kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
    * Install on Debina Linux

      ```text
      curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
      sudo touch /etc/apt/sources.list.d/kubernetes.list
      sudo chmod 753 /etc/apt/sources.list.d/kubernetes.list
      sudo cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
      deb https://apt.kubernetes.io/ kubernetes-xenial main
      EOF
      sudo apt-get update
      sudo apt-get install -y kubelet="1.13.4-00" kubeadm="1.13.4-00" kubectl="1.13.  4-00" kubernetes-cni="0.6.0-00"
      sudo apt-mark hold kubelet kubeadm kubectl kubernetes-cni
      ```

    * initialize the cluster, `sudo kubeadm init --pod-network-cidr=192.168.0.0/16`
      * `--pod-network-cidr` defines the pod IP.
      * run cammand with `--dry-run` will check errors before actually attempting to initialize. Here are some common errors:
        * `[ERROR FileContent--proc-sys-net-bridge-bridge-nf-call-iptables]: /proc/sys/net/bridge/bridge-nf-call-iptables does not exist`. Solution: run `sudo modprobe br_netfilter`
        * `[ERROR Swap]: running with swap on is not supported. Please disable swap`. Solution: run `sudo swapoff -a`
    * Follow the output of the `kubeadm init` to complete further setup including adding nodes to the cluster and defining certificates.
    * Install network add-ons, choose one of the following to install by applying manifests to the cluster.
      * Cilium - `kubectl create -f https://raw.githubusercontent.com/cilium/cilium/v1.4/examples/kubernetes/1.13/cilium.yaml`
      * Calico
* Cloud based Kubernetes services - Provide setting and let the cloud service setup everything
  * GKE - Google Kubernetes Engine
  * AKS - Azure Kubernentes Service
  * Amazon EKS

## Manifest

* A K8s object are defined in manifest files in `YAML` format.
  * Objects are K8s components including `Pod`, `ReplicationController`, `Service`, `Namespace`,`Node` etc.

### Define a Pod Object

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    app: nginx-server
spec:
  containers:
    - name: nginx-custom
      image: [yourDockerHubUsername]/[yourNginxImage]:[yourTag]
      ports:
        - containerPort: 80
```

### Defind a Service

* Setup Cluster IP

  ```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: nginx-service-clusterip
  spec:
    type: "ClusterIP"
    ports:
      - port: 8080
        protocol: TCP
        targetPort: 80
    selector:
      app: nginx-server
  ```

* Setup Node Port

  ```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: nginx-service
  spec:
    type: "NodePort"
    ports:
      - port: 8080
        protocol: TCP
        targetPort: 80
    selector:
      app: nginx-server
  ```

## `kubectl` Commands

* `kubectl explain <object>` or `kubectl explain <object>.<subfield>` will field of a object in a manifest
  * object is any kubernetes object you can define in a manifest
  * `--recursive` will explain objects of sub-fields.
* `kubectl taint nodes --all node-role.kubernetes.io/master-` This removes the "NoSchedule" taint, which then allows the master to think of itself as a worker to form a kubernetes single node cluster.
  * Worker nodes do not have the "NoSchedule" taint.
* `kubectl get nodes` List all nodes in the cluster. Each node is a bare-metal device \(could also be a VM\).
* `kubectl get pods` List pods
* `kubectl get svc` get the status of services
* `kubectl describe svc <ServiceName>` request the details of a service
* `kubectl describe nodes <NodeName>` request the details of a node
* `kubectl describe pods <PodName>` request the details of a node
* `kubectl create -f pod.yaml` create an object from manifest file.
* `kubectl apply -f <FilePath>` apply changes to an object.
* `kubectl delete -f pod.yaml` Remove a object created with the manifest.
* `kubectl delete svc nginx-service-clusterip` delete a service object
  * same as `kubectl delete -f service.yaml`
* `kubectl exec -it <PodName> /bin/bash` Exec into the container

