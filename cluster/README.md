# Cluster

A Kubernetes cluster is the foundation of Kubernetes: a set of machines (nodes) that run containerized workloads together.

It consists of:
- **control-plane node:** manages the cluster state, schedules workloads, exposes the API.
- **worker nodes:** run the actual application Pods.

This directory uses `kind` to create such a cluster locally with one control-plane node and two worker nodes.

## Files

- `cluster.yaml` — kind configuration describing the cluster layout (node roles).
- `cluster.sh` — helper script to create the cluster from that configuration.
