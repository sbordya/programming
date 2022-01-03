K8s (golang) - orchestrator of microservice app, runs on Linux:
* Master (can be multi-master)
    * kube-apiserver
        * front-end (by default port 443)
        * exposes REST api
        * consumes JSON via manifest files
        * kubectl, auth
        * sometimes called master because user interacts with it
    * cluster store
        * persistent storage
        * cluster state and config
        * uses etcd - open source distributed key value store
        * source of truth for the cluster
        * have a backup plan for it
    * kube-controller-manager
        * node controller
        * endpoint controller
        * namespace controller
        * helps maintain the desired state
    * kube-scheduler
        * watches apiserver for new pods
        * assigns work to nodes
        * affinity/anti-affinity
        * constraints
        * resources
* Nodes
    * Kubelet
        * main k8s agent on the node
        * registers node with cluster
        * watches apiserver
        * instanciates pods
        * reports back to master
        * exposes endpoint on port 10255 (/spec, /healthz, /pods)
    * Container engine
        * pulling images
        * starting/stopping containers
        * pluggable: usually Docker, can be rkt (CoreOS)
    * kube-proxy
        * k8s networking
        * each pod has its own ip, containers in the pod share the same ip
        * load balancing across all pods in the service
    * default system pod

Pod - smallest unit of work, scheduling and scaling in k8s
* Network stack
* Kernel namespaces
* n containers
* can't be spread over multiple nodes
* can't be recovered in case of failure, new replica is created
* belongs to the service via labels
* Lifecycle: pending/running/failed/succeded
* apiVersion, kind, metadata (key value pairs), spec.containers (name, image, ports (containerPort))
* kubectl create -f pod.yml
* kubectl get pods; kubectl describe resource

Replication controller (deprecated) - scale pods, desired state, etc

Service - load balancer
* Sends traffic only to healthy pods
* Can be configured for session affinity
* Can point to things outside the cluster
* Random load balancing
* Uses TCP by default
* Has IP, DNS, Port that never changes
* Pod on a node is on port 30050
* Endpoint - list of pods for the server
* Pods update and rollbacks through labels
* ServiceType: 
    * ClusterIP - stable internal cluster IP
    * NodePort - exposes the app outside of the cluster by adding a cluster-wide port on top of ClusterIP
    * LoadBalancer - integrates NodePort with cloud based load balancers
* Command:
    * kubectl expose ...
    * kubectl get ep - endpoints
    * kubectl describe ep name
* Service discovery:
    * DNS based (best)
    * Environment variables (service should be created before pods)


Deployment
* self documenting
* versioned
* spec-once deploy-many
* simple rolling updates and rollbacks (multiple concurrent versions: blue-green deployments/canary releases)
* first class REST objects in the k8s api
* deployed via YAML or JSON manifest
* deployed via the apiserver
* add features to replication controllers (replica sets)

Installation:
* Minikube
    * kubectl
    * VM
        * Localkube (binary): Master + Node
        * Container runtime
    * Commands:
        * install kubectl, minikube
        * minikube config set vm-driver hyperkit
        * minikube start --vm-driver=... --kubernetes-version="v..."
        * kubectl config current-context
        * kubectl get nodes
        * minikube stop
        * minikube delete
* GKE (google kontainer engine aka k8s)
    * Commands:
        * gcloud container clusters list
* kops (aws k8s operations)
    * Install kubectl, kops, aws cli
* kubeadm (manual installation)
