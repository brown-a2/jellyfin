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

## Plugins

Plugins are installed by an init container on pod start (see `plugins` in `values.yaml`).

- **Open Subtitles** - downloaded from the official Jellyfin repo into `/config/plugins/`, md5-verified, skipped if already present. After first install, set your OpenSubtitles.com credentials in Dashboard > Plugins > Open Subtitles (persisted on the config volume).

When upgrading Jellyfin, bump `image.tag` and each plugin's `version`/`checksum` together. Plugin versions must match the server's ABI - check `targetAbi` in https://repo.jellyfin.org/files/plugin/manifest.json
