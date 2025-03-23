# Essential Kubernetes Commands

## Core kubectl Commands
- `kubectl get` - List resources
- `kubectl describe` - Show detailed information about resources
- `kubectl create` - Create resources
- `kubectl apply` - Apply configurations to resources
- `kubectl delete` - Delete resources
- `kubectl exec` - Execute commands in containers
- `kubectl logs` - View container logs
- `kubectl cp` - Copy files between containers and local filesystem
- `kubectl port-forward` - Forward local ports to pod ports
- `kubectl explain` - Documentation for resource types

## YAML Generation Commands
- `kubectl create [resource] --dry-run=client -o yaml` - Generate YAML template without creating the resource
- `kubectl get [resource] [name] -o yaml` - Get existing resource as YAML
- `kubectl run nginx --image=nginx --dry-run=client -o yaml` - Generate pod YAML template
- `kubectl run static-busybox --image=busybox --dry-run=client  -o yaml -- sleep 1000` - Generate pod YAML template with arg
- `kubectl create deployment nginx --image=nginx --dry-run=client -o yaml` - Generate deployment YAML template
- `kubectl create service clusterip my-svc --tcp=80:80 --dry-run=client -o yaml` - Generate service YAML template

## Pod Management
- `kubectl run` - Create and run pods
- `kubectl get pods` - List pods
- `kubectl describe pod` - Show pod details
- `kubectl logs` - View pod logs
- `kubectl exec -it [pod] -- /bin/bash` - Shell into a pod

## Deployment Management
- `kubectl create deployment` - Create deployments
- `kubectl scale deployment` - Scale deployments
- `kubectl rollout status` - Check rollout status
- `kubectl rollout history` - View rollout history
- `kubectl rollout undo` - Rollback to previous version

## Configuration
- `kubectl create configmap` - Create ConfigMaps
- `kubectl create secret` - Create Secrets
- `kubectl label` - Add or update labels
- `kubectl annotate` - Add or update annotations
- `kubectl taint` - Add or remove taints on nodes

## Cluster Management
- `kubectl get nodes` - List nodes
- `kubectl cordon/uncordon` - Mark node as unschedulable/schedulable
- `kubectl drain` - Safely evict pods from node
- `kubectl taint nodes` - Set taints on nodes
- `kubectl top` - Show resource usage (CPU/memory)

## Namespace Management
- `kubectl create namespace` - Create namespaces
- `kubectl config set-context --current --namespace=` - Change current namespace

## Service & Networking
- `kubectl expose` - Expose deployments as services
- `kubectl get services` - List services
- `kubectl get endpoints` - List endpoints

## ETCD Backup/Restore
- `etcdctl snapshot save` - Create ETCD snapshot
- `etcdctl snapshot restore` - Restore from snapshot

## Troubleshooting
- `kubectl get events` - View cluster events
- `kubectl describe` - Detailed resource inspection
- `kubectl logs` - Container logs
- `kubectl exec` - Run commands in containers
- `crictl` - Interact with container runtime

## Kubectl Context and Configuration
- `kubectl config view` - View kubeconfig
- `kubectl config use-context` - Switch contexts
- `kubectl config set-context` - Create/modify contexts