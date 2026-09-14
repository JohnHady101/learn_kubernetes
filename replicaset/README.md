# ReplicaSet

A ReplicaSet is a Kubernetes controller that maintains a stable set of identical Pods.

It ensures a defined number of replicas are always running: if a Pod crashes or is deleted, the ReplicaSet starts a replacement; if there are too many, it removes extras. It works with a selector to find matching Pods and a pod template to create new ones when needed.

This directory contains an example that keeps three identical nginx Pods running.

## Files

- `replicaset.yaml` — ReplicaSet definition `nginx-replicaset` with desired count `3`, selector `app: nginx`, and a pod template for nginx.
- `replicaset.sh` — helper script to create the ReplicaSet from the yaml definition.
- `describe_replica.sh` — helper script to inspect the ReplicaSet status and events.
