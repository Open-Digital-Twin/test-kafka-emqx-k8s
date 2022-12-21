# Kafka on Kubernetes for local development

https://dev.to/thegroo/running-kafka-on-kubernetes-for-local-development-with-storage-class-4oa9

This document explains running single node local kafka infra on kubernetes it covers kafka, zookeeper and
schema-registry in kubernetes using [Kind](https://kind.sigs.k8s.io/).

### Pre-reqs, install:

- [Docker](https://docs.docker.com/get-docker/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)
- [Kind](https://kind.sigs.k8s.io/)
- [Helm](https://helm.sh/) - Only required if you want to run the Helm setup.

### Step-by-step to running with Helm

1. Open a terminal and cd to helm folder
<!-- 2. Start Kind running: `kind create cluster --config=kind-config.yml` -->
3. Run `helm install ${pick_a_name} local-kafka-dev`. i.e - `helm install local-kafka local-kafka-dev`
4. When done stop kafka setup using `helm uninstall ${name_picked_step_3}`, you may also stop Kind if you want: `kind delete cluster`

## Useful kubectl commands

Check kubernetes pods, services, volumes health:

 - `kubectl get pods` - a list of all pods
 - `kubectl get svc` - a list of all services
 - `kubectl get pv` - a list of all persistent volumes
 - `kubectl get pvc` - a list of all persistent volume claims
 - `kubectl describe pod $pod_name` - describe a specific pod
 - `kubectl logs $pod_name` - get logs for a specific pod
 - `kubectl exec -it $pod_name -- bash` - enters container and run a bash shell in a specific pod

> The last command opens a terminal session in a running kubernetes container with bash context. Use `exit` to quit.

## Stop kubernetes and kind

- `kubectl delete -f kafka-local-config`
- `kind delete cluster`





## More commands

- `kubectl delete all --all -n fpknebel` - delete everything from namespace
- `kubectl delete pvc --all -n fpknebel` - delete all PVC from namespace