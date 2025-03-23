## Core kubectl Commands
- `kubectl get` - List resources
  - Description: Display one or many resources
  - Example: `kubectl get pods -n dev-namespace`
- `kubectl describe` - Show detailed information about resources
  - Description: Show detailed state of one or many resources
  - Example: `kubectl describe pod nginx-pod`
- `kubectl create` - Create resources
  - Description: Create a resource from a file or from stdin
  - Example: `kubectl create deployment nginx --image=nginx`
- `kubectl apply` - Apply configurations to resources
  - Description: Apply a configuration to a resource by file name or stdin
  - Example: `kubectl apply -f deployment.yaml`
- `kubectl delete` - Delete resources
  - Description: Delete resources by file names, stdin, resources and names, or by resources and label selector
  - Example: `kubectl delete pod nginx-pod`
- `kubectl exec` - Execute commands in containers
  - Description: Execute a command in a container
  - Example: `kubectl exec -it nginx-pod -- /bin/bash`
- `kubectl logs` - View container logs
  - Description: Print the logs for a container in a pod
  - Example: `kubectl logs nginx-pod`
- `kubectl cp` - Copy files between containers and local filesystem
  - Description: Copy files and directories to and from containers
  - Example: `kubectl cp nginx-pod:/etc/nginx/nginx.conf ./nginx.conf`
- `kubectl port-forward` - Forward local ports to pod ports
  - Description: Forward one or more local ports to a pod
  - Example: `kubectl port-forward pod/nginx-pod 8080:80`
- `kubectl explain` - Documentation for resource types
  - Description: Get documentation for a resource and its fields
  - Example: `kubectl explain pods.spec.containers`

## YAML Generation Commands
- `kubectl create [resource] --dry-run=client -o yaml` - Generate YAML template without creating the resource
  - Description: Generate resource YAML file without sending it to the server
  - Example: `kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deployment.yaml`
- `kubectl get [resource] [name] -o yaml` - Get existing resource as YAML
  - Description: Export existing resource in YAML format
  - Example: `kubectl get deployment nginx -o yaml > existing-deployment.yaml`
- `kubectl run nginx --image=nginx --dry-run=client -o yaml` - Generate pod YAML template
  - Description: Generate a pod YAML definition quickly without creating it
  - Example: `kubectl run nginx --image=nginx --port=80 --dry-run=client -o yaml > nginx-pod.yaml`
- `kubectl run static-busybox --image=busybox --dry-run=client  -o yaml -- sleep 1000` - Generate pod YAML template with arg
  - Description: Generate a pod YAML definition with command arguments
  - Example: `kubectl run debug-pod --image=busybox --dry-run=client -o yaml -- sleep 3600 > debug-pod.yaml`
- `kubectl create deployment nginx --image=nginx --dry-run=client -o yaml` - Generate deployment YAML template
  - Description: Generate a deployment YAML definition
  - Example: `kubectl create deployment webapp --image=nginx:1.20 --replicas=3 --dry-run=client -o yaml > webapp-deployment.yaml`
- `kubectl create service clusterip my-svc --tcp=80:80 --dry-run=client -o yaml` - Generate service YAML template
  - Description: Generate a service YAML definition quickly
  - Example: `kubectl create service clusterip frontend --tcp=80:8080 --dry-run=client -o yaml > frontend-svc.yaml`

## Pod Management
- `kubectl run` - Create and run pods
  - Description: Create and run a particular image in a pod
  - Example: `kubectl run nginx --image=nginx --port=80`
- `kubectl get pods` - List pods
  - Description: List all pods in the current namespace
  - Example: `kubectl get pods --all-namespaces`
- `kubectl describe pod` - Show pod details
  - Description: Show detailed information about a specific pod
  - Example: `kubectl describe pod nginx-pod`
- `kubectl logs` - View pod logs
  - Description: Print the logs for a pod's containers
  - Example: `kubectl logs -f nginx-pod`
- `kubectl exec -it [pod] -- /bin/bash` - Shell into a pod
  - Description: Get an interactive shell to a running container
  - Example: `kubectl exec -it nginx-pod -- /bin/bash`

## Deployment Management
- `kubectl create deployment` - Create deployments
  - Description: Create a deployment with specified containers
  - Example: `kubectl create deployment nginx --image=nginx --replicas=3`
- `kubectl scale deployment` - Scale deployments
  - Description: Set a new size for a deployment
  - Example: `kubectl scale deployment nginx --replicas=5`
- `kubectl rollout status` - Check rollout status
  - Description: Monitor the status of a rollout
  - Example: `kubectl rollout status deployment/nginx`
- `kubectl rollout history` - View rollout history
  - Description: View the rollout history of a deployment
  - Example: `kubectl rollout history deployment/nginx`
- `kubectl rollout undo` - Rollback to previous version
  - Description: Rollback to a previous deployment revision
  - Example: `kubectl rollout undo deployment/nginx`

## Configuration
- `kubectl create configmap` - Create ConfigMaps
  - Description: Create a ConfigMap from file, directory, or literal values
  - Example: `kubectl create configmap app-config --from-file=config.properties`
- `kubectl create secret` - Create Secrets
  - Description: Create a secret using specified subcommand
  - Example: `kubectl create secret generic db-creds --from-literal=username=admin --from-literal=password=s3cr3t`
- `kubectl label` - Add or update labels
  - Description: Update the labels on a resource
  - Example: `kubectl label pods nginx-pod env=prod`
- `kubectl annotate` - Add or update annotations
  - Description: Update the annotations on a resource
  - Example: `kubectl annotate pods nginx-pod description="Frontend web server"`
- `kubectl taint` - Add or remove taints on nodes
  - Description: Update the taints on one or more nodes
  - Example: `kubectl taint nodes worker-1 key=value:NoSchedule`

## Cluster Management
- `kubectl get nodes` - List nodes
  - Description: List all nodes in the cluster
  - Example: `kubectl get nodes -o wide`
- `kubectl cordon/uncordon` - Mark node as unschedulable/schedulable
  - Description: Mark node as unschedulable/schedulable
  - Example: `kubectl cordon worker-1`
- `kubectl drain` - Safely evict pods from node
  - Description: Drain node in preparation for maintenance
  - Example: `kubectl drain worker-1 --ignore-daemonsets`
- `kubectl taint nodes` - Set taints on nodes
  - Description: Add taints to nodes that affect scheduling
  - Example: `kubectl taint nodes worker-1 dedicated=gpu:NoSchedule`
- `kubectl top` - Show resource usage (CPU/memory)
  - Description: Display resource usage (CPU/memory) of nodes or pods
  - Example: `kubectl top nodes`

## Namespace Management
- `kubectl create namespace` - Create namespaces
  - Description: Create a new namespace with the specified name
  - Example: `kubectl create namespace development`
- `kubectl config set-context --current --namespace=` - Change current namespace
  - Description: Set the default namespace for kubectl commands
  - Example: `kubectl config set-context --current --namespace=kube-system`

## Service & Networking
- `kubectl expose` - Expose deployments as services
  - Description: Expose a resource as a Kubernetes service
  - Example: `kubectl expose deployment nginx --port=80 --type=NodePort`
- `kubectl get services` - List services
  - Description: List all services in the namespace
  - Example: `kubectl get svc -o wide`
- `kubectl get endpoints` - List endpoints
  - Description: List all endpoints for services
  - Example: `kubectl get endpoints kubernetes`

## ETCD Backup/Restore
- `etcdctl snapshot save` - Create ETCD snapshot
  - Description: Save a snapshot of the etcd database
  - Example: `ETCDCTL_API=3 etcdctl --endpoints=https://127.0.0.1:2379 --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key snapshot save /backup/etcd-snapshot.db`
- `etcdctl snapshot restore` - Restore from snapshot
  - Description: Restore an etcd cluster from a snapshot
  - Example: `ETCDCTL_API=3 etcdctl snapshot restore /backup/etcd-snapshot.db --data-dir=/var/lib/etcd-restore`

## Troubleshooting
- `kubectl get events` - View cluster events
  - Description: List events in the current namespace
  - Example: `kubectl get events --sort-by=.metadata.creationTimestamp`
- `kubectl describe` - Detailed resource inspection
  - Description: Get detailed info for troubleshooting
  - Example: `kubectl describe pod nginx-pod`
- `kubectl logs` - Container logs
  - Description: View logs for debugging containers
  - Example: `kubectl logs -f deployment/nginx`
- `kubectl exec` - Run commands in containers
  - Description: Execute commands for diagnostics
  - Example: `kubectl exec -it nginx-pod -- curl localhost`
- `crictl` - Interact with container runtime
  - Description: Debug container runtime issues
  - Example: `crictl ps`

## Kubectl Context and Configuration
- `kubectl config view` - View kubeconfig
  - Description: Display merged kubeconfig settings
  - Example: `kubectl config view --minify`
- `kubectl config use-context` - Switch contexts
  - Description: Set the current context in a kubeconfig file
  - Example: `kubectl config use-context production`
- `kubectl config set-context` - Create/modify contexts
  - Description: Set a context entry in kubeconfig
  - Example: `kubectl config set-context --current --namespace=default`