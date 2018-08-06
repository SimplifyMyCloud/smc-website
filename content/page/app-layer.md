---
title: App Layer
subtitle: Application and Service Orchestration
comments: false
---

## Description
---

*The goal of the App Layer is the orchestration of applications and services running on the Service Layer.*

---

The App Layer enables developers to experiment freely with new ideas, without asking for approval to use an already approved service.  Once Kubernetes is approved and deployed into the infrastructure state, a dev can freely deploy into Kubernetes by simply adding a Helm chart to the App Layer git repo, allowing Ansible to then deploy into the environment.

---

## App Layer Empathy:
  - dev empathy by providing freedom to tinker on already deployed services
  - ops empathy by knowing that services being deployed into have already been configured for logging, monitoring, observability, and right-sized
  - business empathy by allowing for demo environments to be deployed with just access to [Ansible Tower](https://www.ansible.com/products/tower), and a few buttons clicked

---

This layers infrastructure state is ensured using [Ansible](https://www.ansible.com/).  This project has the strong opinion that Ansible is the best tool to orchestrate across the App Layer.  As Ansible can perform tasks the chain and perform them in order, Ansible is the perfect tool to deploy applications and services across the App Layer. See the App Layer [README](https://github.com/SimplifyMyCloud/SMCInfrastructureState/blob/gcp_app/AppLayer/README.md) for coding standards and naming conventions along with requirements.

---

## App Layer contents:
  - Binary baked compute instances
  - Container baked instances
  - Helm Charts

---

## Descriptions:
  
  - *Binary baked compute instances*
    
    "Baked" refers to the process of using an automated build systems to snapshot the OS after the application binary has been installed and configured on the compute instance.  Once the instance is fully configured and ready to run in an environment, it is snapshotted, *aka baked*, and stored as a *immutable object* that can be deployed and booted, with a known and expected instance state that cannot, and will not, be changed once deployed to the environment.  All baked instances are versioned using [SemVer](https://semver.org/), any changes necessary to the baked instance, would require a bump in version number of the instance object.
  
  ---

  - *Container baked instances*
    
    A baked container instance is best practices when using a container optimized OS like [CoreOS](https://coreos.com/), [RancherOS](https://rancher.com/rancher-os/), or [Google Container Optimized OS](https://cloud.google.com/container-optimized-os/).  Since these OS's are typically read-only file systems, they are baked by default.  The only change that occurs is configuring which container to pull and run on the OS boot.
  
  ---

  - *Helm Charts*
    
    [Helm](https://helm.sh/) charts are used to deploy, and orchestrate, applications and services into Kubernetes.  Kubernetes will already be running as ensured by the Service Layer, and ready to accept Helm charts.  Other Kubernetes deployment methods can be used but this repo has the strong opinion on Helm.
