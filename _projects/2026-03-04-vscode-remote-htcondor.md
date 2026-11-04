---
title: 'vscode-remote-htcondor'
subtitle: 'VS Code on HTCondor compute nodes'
date: 2026-03-04 00:00:00
featured_image: /images/fraimondo/rio_v.jpeg
project_image: '/images/projects/vscode_remote_htcondor_logo.svg'
image_size: contain
excerpt: Connect VS Code to an HTCondor compute node in one click, straight from the Remote Explorer.
publish: true
---

vscode-remote-htcondor connects [VS Code](https://code.visualstudio.com) to a compute node of an [HTCondor](https://htcondor.org) cluster, straight from the Remote Explorer. It works with the [Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) extension.

- Starts a job on a compute node if none is running, then connects to it.
- Runs automatically through SSH's `ProxyCommand`, so there is no script to run by hand on the cluster.
- Cancels the job when you disconnect, so idle sessions don't hold on to cluster resources.

To install, log in to your cluster's login node and run:

```shell
curl -fsSLO https://raw.githubusercontent.com/fraimondo/vscode-remote-htcondor/refs/heads/main/install.sh && $SHELL install.sh
```

The cluster has to meet a few requirements, for example `sshd` must be available on the compute nodes. See the README for the full list.

- [Source code and README on GitHub](https://github.com/fraimondo/vscode-remote-htcondor)
