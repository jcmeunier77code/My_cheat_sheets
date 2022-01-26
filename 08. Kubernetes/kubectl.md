# kubectl

kubectl controls the Kubernetes cluster manager.

Find more information at: https://kubernetes.io/docs/reference/kubectl/overview/

<details><summary>See basic comands</summary>
<p>

```shell
Basic Commands (Beginner):
  create        Create a resource from a file or from stdin
  expose        Take a replication controller, service, deployment or pod and expose it as a new Kubernetes service
  run           Run a particular image on the cluster
  set           Set specific features on objects

Basic Commands (Intermediate):
  explain       Get documentation for a resource
  get           Display one or many resources
  edit          Edit a resource on the server
  delete        Delete resources by file names, stdin, resources and names, or by resources and label selector

Deploy Commands:
  rollout       Manage the rollout of a resource
  scale         Set a new size for a deployment, replica set, or replication controller
  autoscale     Auto-scale a deployment, replica set, stateful set, or replication controller

Cluster Management Commands:
  certificate   Modify certificate resources.
  cluster-info  Display cluster information
  top           Display resource (CPU/memory) usage
  cordon        Mark node as unschedulable
  uncordon      Mark node as schedulable
  drain         Drain node in preparation for maintenance
  taint         Update the taints on one or more nodes

Troubleshooting and Debugging Commands:
  describe      Show details of a specific resource or group of resources
  logs          Print the logs for a container in a pod
  attach        Attach to a running container
  exec          Execute a command in a container
  port-forward  Forward one or more local ports to a pod
  proxy         Run a proxy to the Kubernetes API server
  cp            Copy files and directories to and from containers
  auth          Inspect authorization
  debug         Create debugging sessions for troubleshooting workloads and nodes

Advanced Commands:
  diff          Diff the live version against a would-be applied version
  apply         Apply a configuration to a resource by file name or stdin
  patch         Update fields of a resource
  replace       Replace a resource by file name or stdin
  wait          Experimental: Wait for a specific condition on one or many resources
  kustomize     Build a kustomization target from a directory or URL.

Settings Commands:
  label         Update the labels on a resource
  annotate      Update the annotations on a resource
  completion    Output shell completion code for the specified shell (bash or zsh)

Other Commands:
  api-resources Print the supported API resources on the server
  api-versions  Print the supported API versions on the server, in the form of "group/version"
  config        Modify kubeconfig files
  plugin        Provides utilities for interacting with plugins
  version       Print the client and server version information

Usage:
  kubectl [flags] [options]

Use "kubectl <command> --help" for more information about a given command.
Use "kubectl options" for a list of global command-line options (applies to all commands).
```

</p>
</details>

# Minikube

minikube provisions and manages local Kubernetes clusters optimized for development workflows.

Find more information at: https://minikube.sigs.k8s.io/docs/start/

<details><summary>See basic comands</summary>
<p>

```shell
Basic Commands:
  start          Starts a local Kubernetes cluster
  status         Gets the status of a local Kubernetes cluster
  stop           Stops a running local Kubernetes cluster
  delete         Deletes a local Kubernetes cluster
  dashboard      Access the Kubernetes dashboard running within the minikube cluster
  pause          pause Kubernetes
  unpause        unpause Kubernetes

Images Commands:
  docker-env     Configure environment to use minikube's Docker daemon
  podman-env     Configure environment to use minikube's Podman service
  cache          Add, delete, or push a local image into minikube
  image          Manage images

Configuration and Management Commands:
  addons         Enable or disable a minikube addon
  config         Modify persistent configuration values
  profile        Get or list the current profiles (clusters)
  update-context Update kubeconfig in case of an IP or port change

Networking and Connectivity Commands:
  service        Returns a URL to connect to a service
  tunnel         Connect to LoadBalancer services

Advanced Commands:
  mount          Mounts the specified directory into minikube
  ssh            Log into the minikube environment (for debugging)
  kubectl        Run a kubectl binary matching the cluster version
  node           Add, remove, or list additional nodes
  cp             Copy the specified file into minikube

Troubleshooting Commands:
  ssh-key        Retrieve the ssh identity key path of the specified node
  ssh-host       Retrieve the ssh host key of the specified node
  ip             Retrieves the IP address of the specified node
  logs           Returns logs to debug a local Kubernetes cluster
  update-check   Print current and latest version number
  version        Print the version of minikube
  options        Show a list of global command-line options (applies to all commands).

Other Commands:
  completion     Generate command completion for a shell

Use "minikube <command> --help" for more information about a given command.
```
 
  
</p>
</details>
  
## Starting minikube 

### Create minikube cluster

starting minikube with docker specified 
```shell
minikube start --driver=docker
```

check the status of the nodes 
```shell
kubectl get nodes 
```

check if minikube is running
```shell
minikube status
```

check kubernetes version 
```shell
kubectl version
```

kubectl cli: for configuring the minikube cluster 
minikube cli: for stating/deleting the cluster

### delete cluster and restart in debug mode
`minikube delete`

`minikube start --vm-driver=hyperkit --v=7 --alsologtostderr`

`minikube status`

### kubectl commands
`kubectl get nodes`

`kubectl get pod`

`kubectl get services`

`kubectl create deployment nginx-depl --image=nginx`  
see, for details on nginx example: https://www.nginx.com/

usage:
`kubectl create deployment NAME --image=IMAGE [--DRY-RUN] [options]`

kubectl create details 
```shell
Create a resource from a file or from stdin.

 JSON and YAML formats are accepted.

Examples:
  # Create a pod using the data in pod.json
  kubectl create -f ./pod.json

  # Create a pod based on the JSON passed into stdin
  cat pod.json | kubectl create -f -

  # Edit the data in docker-registry.yaml in JSON then create the resource using the edited data
  kubectl create -f docker-registry.yaml --edit -o json

Available Commands:
  clusterrole         Create a cluster role
  clusterrolebinding  Create a cluster role binding for a particular cluster role
  configmap           Create a config map from a local file, directory or literal value
  cronjob             Create a cron job with the specified name
  deployment          Create a deployment with the specified name
  ingress             Create an ingress with the specified name
  job                 Create a job with the specified name
  namespace           Create a namespace with the specified name
  poddisruptionbudget Create a pod disruption budget with the specified name
  priorityclass       Create a priority class with the specified name
  quota               Create a quota with the specified name
  role                Create a role with single rule
  rolebinding         Create a role binding for a particular role or cluster role
  secret              Create a secret using specified subcommand
  service             Create a service using a specified subcommand
  serviceaccount      Create a service account with the specified name

Options:
      --allow-missing-template-keys=true: If true, ignore any errors in templates when a field or map key is missing in
the template. Only applies to golang and jsonpath output formats.
      --dry-run='none': Must be "none", "server", or "client". If client strategy, only print the object that would be
sent, without sending it. If server strategy, submit server-side request without persisting the resource.
      --edit=false: Edit the API resource before creating
      --field-manager='kubectl-create': Name of the manager used to track field ownership.
  -f, --filename=[]: Filename, directory, or URL to files to use to create the resource
  -k, --kustomize='': Process the kustomization directory. This flag can't be used together with -f or -R.
  -o, --output='': Output format. One of:
json|yaml|name|go-template|go-template-file|template|templatefile|jsonpath|jsonpath-as-json|jsonpath-file.
      --raw='': Raw URI to POST to the server.  Uses the transport specified by the kubeconfig file.
  -R, --recursive=false: Process the directory used in -f, --filename recursively. Useful when you want to manage
related manifests organized within the same directory.
      --save-config=false: If true, the configuration of current object will be saved in its annotation. Otherwise, the
annotation will be unchanged. This flag is useful when you want to perform kubectl apply on this object in the future.
  -l, --selector='': Selector (label query) to filter on, supports '=', '==', and '!='.(e.g. -l key1=value1,key2=value2)
      --show-managed-fields=false: If true, keep the managedFields when printing objects in JSON or YAML format.
      --template='': Template string or path to template file to use when -o=go-template, -o=go-template-file. The
template format is golang templates [http://golang.org/pkg/text/template/#pkg-overview].
      --validate=true: If true, use a schema to validate the input before sending it
      --windows-line-endings=true: Only relevant if --edit=true. Defaults to the line ending native to your platform.

Usage:
  kubectl create -f FILENAME [options]
```

get information on deployment and on pod created 
```shell
kubectl get deployment
kubectl get pods
```

replicaset: function to manage the replicas of a pod (done automatically)
`kubectl get replicaset`
ex. pod name : 
nginx-depl-5ddc44dd46-zzncg
namecreated-replicasetID-podID
ex. id replicaset: nginx-depl-5ddc44dd46


`kubectl edit deployment nginx-depl`
-- auto-generated configuration file with default values 


### debugging
`kubectl logs {pod-name}`

`kubectl exec -it {pod-name} -- bin/bash`
-- to execute the pod within powershell
-- user become root and can enter the container/pod 
-- to exit 'exit'
-- see as example 

```shell
PS C:\Users\jcmeu> kubectl exec -it mongo-depl-85ddc6d66-7hsrn -- bin/bash
root@mongo-depl-85ddc6d66-7hsrn:/# ls
bin   data  docker-entrypoint-initdb.d  home        lib    lib64   media  opt   root  sbin  sys  usr
boot  dev   etc                         js-yaml.js  lib32  libx32  mnt    proc  run   srv   tmp  var
root@mongo-depl-85ddc6d66-7hsrn:/# exit
exit
PS C:\Users\jcmeu>
```



### create mongo deployment
`kubectl create deployment mongo-depl --image=mongo`

`kubectl logs mongo-depl-{pod-name}`

`kubectl describe pod mongo-depl-{pod-name}`

details given by describe function 
```shell
PS C:\Users\jcmeu> kubectl describe pod mongo-depl-85ddc6d66-7hsrn
Name:         mongo-depl-85ddc6d66-7hsrn
Namespace:    default
Priority:     0
Node:         minikube/192.168.49.2
Start Time:   Wed, 26 Jan 2022 16:44:15 +0100
Labels:       app=mongo-depl
              pod-template-hash=85ddc6d66
Annotations:  <none>
Status:       Running
IP:           172.17.0.3
IPs:
  IP:           172.17.0.3
Controlled By:  ReplicaSet/mongo-depl-85ddc6d66
Containers:
  mongo:
    Container ID:   docker://3a242651af8f047a0df0409193a7aef665fc7b3e9a5910c1ee39c504f83979e2
    Image:          mongo
    Image ID:       docker-pullable://mongo@sha256:079089900e9511a782a59a4276046835189720eb668088869d147d1145cebe14
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Wed, 26 Jan 2022 16:44:32 +0100
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-9rvb7 (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  kube-api-access-9rvb7:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  8m23s  default-scheduler  Successfully assigned default/mongo-depl-85ddc6d66-7hsrn to minikube
  Normal  Pulling    8m22s  kubelet            Pulling image "mongo"
  Normal  Pulled     8m6s   kubelet            Successfully pulled image "mongo" in 16.059475036s
  Normal  Created    8m6s   kubelet            Created container mongo
  Normal  Started    8m6s   kubelet            Started container mongo
```

### delete deplyoment
`kubectl delete deployment mongo-depl`

`kubectl delete deployment nginx-depl`

see example for details 
```shell
PS C:\Users\jcmeu> kubectl get deployment
NAME         READY   UP-TO-DATE   AVAILABLE   AGE
mongo-depl   1/1     1            1           38m
nginx-depl   1/1     1            1           65m
PS C:\Users\jcmeu> kubectl get pod
NAME                          READY   STATUS    RESTARTS   AGE
mongo-depl-85ddc6d66-7hsrn    1/1     Running   0          38m
nginx-depl-7d459cf5c8-v8m4d   1/1     Running   0          46m
PS C:\Users\jcmeu> kubectl delete deployment nginx-depl
deployment.apps "nginx-depl" deleted
PS C:\Users\jcmeu> kubectl get deployment
NAME         READY   UP-TO-DATE   AVAILABLE   AGE
mongo-depl   1/1     1            1           41m
PS C:\Users\jcmeu> kubectl get pod
NAME                         READY   STATUS    RESTARTS   AGE
mongo-depl-85ddc6d66-7hsrn   1/1     Running   0          41m
PS C:\Users\jcmeu> kubectl get replicaset
NAME                   DESIRED   CURRENT   READY   AGE
mongo-depl-85ddc6d66   1         1         1       42m
PS C:\Users\jcmeu>
```


### create or edit config file
When creating a deployment (create command) you cannot set up all the configurations/options in one line.
Therefore, easier to work with ConfigFile which contains all the options and configuration. 

`vim nginx-deployment.yaml`

`kubectl apply -f nginx-deployment.yaml`

`kubectl get pod`

`kubectl get deployment`

### delete with config
`kubectl delete -f nginx-deployment.yaml`

### Metrics

`kubectl top` The kubectl top command returns current CPU and memory usage for a cluster’s pods or nodes, or for a particular pod or node if specified.


```shell

```

```shell

```

```shell

```

```shell

```






## Main commands

