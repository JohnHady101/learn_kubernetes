# Pods

A Pod is the smallest deployable unit in Kubernetes.

It wraps one or more containers that share the same network, IP address, and storage volumes, so they can communicate as if running on the same machine. Pods are ephemeral: if a Pod dies, it is not revived — a new one replaces it. That is why higher-level controllers like ReplicaSets are used for long-running workloads.

This directory contains a simple example Pod running nginx.

## Files

- `nginx.yaml` — Pod definition named `nginx` with label `app: nginx`, running a single nginx container.
- `pod.sh` — helper script to create that Pod from the yaml definition.
