## Learn Kubernetes

Small learning repo for the main Kubernetes building blocks: cluster, pods, and ReplicaSets. Each directory holds yaml definitions plus helper shell scripts (see the shell files for the exact commands).

### Cluster (`cluster/`)

A Kubernetes cluster is the foundation: a set of machines (nodes) that run containerized workloads together.

- **control-plane node:** manages cluster state, schedules workloads, exposes the API.
- **worker nodes:** run the actual application Pods.

This repo creates a local cluster with one control-plane node and two worker nodes.

Files:
- `cluster/cluster.yaml` — cluster layout (node roles).
- `cluster/cluster.sh` — helper script to create the cluster from that configuration.

### Pods (`pods/`)

A Pod is the smallest deployable unit in Kubernetes.

It wraps one or more containers sharing the same network, IP, and storage, so they communicate as if on the same machine. Pods are ephemeral: if one dies it is not revived, a new one replaces it — hence controllers like ReplicaSets for long-running workloads.

Files:
- `pods/nginx.yaml` — example Pod `nginx` (label `app: nginx`) running a single nginx container.
- `pods/pod.sh` — helper script to create that Pod from the yaml definition.

### ReplicaSet (`replicaset/`)

A ReplicaSet is a controller that maintains a stable set of identical Pods.

It keeps a defined replica count always running: on crash/deletion it starts a replacement, on excess it removes extras. It uses a selector to find matching Pods and a pod template to create new ones.

This repo keeps three identical nginx Pods running.

Files:
- `replicaset/replicaset.yaml` — ReplicaSet `nginx-replicaset`, desired count `3`, selector `app: nginx`, nginx pod template.
- `replicaset/replicaset.sh` — helper script to create the ReplicaSet.
- `replicaset/describe_replica.sh` — helper script to inspect its status and events.

### Deployment (`deployment/`)

A Deployment is a higher-level controller that manages ReplicaSets and enables rolling updates, rollbacks, and scaling for stateless workloads.

It defines a desired state (replica count, pod template, resources) and progressively updates Pods without downtime.

Files:
- `deployment/deployment.yaml` — Deployment `nginx-deployment` with `3` replicas, selector `app: nginx`, nginx pod template with CPU/memory requests and limits.
- `deployment/deployment.sh` — helper script to create the Deployment from the yaml definition.