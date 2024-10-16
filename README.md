# Jellyfin k8s build

Using Helm, this Chart builds an instance of Jellyfin to run on a kubernetes cluster (k3s) running on a pi5.

## Installation

Required
- K8s environment
- Helm
- PI Bookworm OS

Paths required
`/srv/jellyfin/config` - on the pi's local storage
`/mnt/nvme4tb` - ssh nvme external storage

Launch using Helm
`helm install jellyfin . --namespace jellyfin --create-namespace`


