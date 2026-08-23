# Raspberry Pi K3s Homelab

A self-hosted Kubernetes homelab running on a Raspberry Pi 5, using **K3s** and **Flux CD** to manage application deployment through GitOps.

The cluster currently runs a bookmark application and is designed as a hands-on environment for learning and applying Kubernetes, GitOps, Linux administration, container security, persistent storage, and secure remote access.

## Architecture

* **Hardware:** Raspberry Pi 5
* **Kubernetes:** K3s
* **GitOps:** Flux CD
* **Configuration:** Kubernetes manifests managed in Git
* **Storage:** Kubernetes PersistentVolumeClaim
* **Container security:** Application runs as a non-root user
* **Remote access:** Cloudflare Tunnel
* **Server access:** SSH key-based authentication
* **Repository:** Public GitHub repository

## GitOps Workflow

Flux CD continuously monitors this repository and reconciles the Kubernetes configuration with the running K3s cluster.

```text
GitHub Repository
       │
       │  configuration changes
       ▼
   Flux CD
       │
       │  reconciliation
       ▼
 Raspberry Pi 5 - K3s
       |
       │
       ▼
 Bookmark Application
       │
       ▼
 Persistent Storage
```

This allows infrastructure and deployment configuration to be managed through Git rather than manually applying changes to the cluster.

## Security

The cluster is designed with several basic security practices:

* The application container runs as a non-root user.
* SSH access uses key-based authentication rather than passwords.
* The application is accessible remotely through a Cloudflare Tunnel.
* No inbound port is opened on the home router for application access.

## Storage

The bookmark application uses a **Kubernetes PersistentVolumeClaim** for persistent application data, allowing data to remain available across pod replacement.

## Repository Structure

```text
apps/
└── ...

clusters/
└── staging/
    └── ...
```

The repository contains the Kubernetes and Flux configuration used to manage the homelab rather than the application's source code.

## Why This Project?

This homelab is a practical environment for developing infrastructure and DevOps skills through hands-on work rather than isolated tutorials. It provides experience with Kubernetes deployment, GitOps workflows, persistent storage, container security, Linux administration, and secure remote access on real hardware.

## Status

The cluster is actively maintained and the bookmark application is usable whenever the Raspberry Pi is running.
