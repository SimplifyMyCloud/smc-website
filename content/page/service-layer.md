---
title: Service Layer
subtitle: Ensure the Services to Service the Applications
comments: false
---


*The goal of the Service Layer is the ensured state of services needed to run the applications in the App Layer.*

---

The Service Layer enables the DevOps culture within the company.  If developers are writing applications and operations are ensuring the state of the cloud, the Service layer is where those two teams meet.  If the developers are wrapping their application in a `rkt` container, operations are responsible for wiring up the Kubernetes service into the cloud.  *Wiring up* a service consists of ensuring logging, monitoring, observability, redundancy, and of course automation.  Once a service is ensured to be available, the developers are then freed to experiment by launching into a service that they know is wired into the cloud.  If a developer needs to launch a brand new service, a pull request that is approved by development *and* operations required.  This gives the operations team the opportunity to verify or build into the *wiring* for that service.  A discussion can then happen between development and operations on how to solve that problem with what available service.

---

## Service Layer Empathy:
  - dev empathy by providing already wired in services to then consume
  - ops empathy by allowing the proper wiring to be completed before releasing the service to the business
  - business empathy by knowing that services being used have been agreed upon and correctly configured by both operations and development to be redundant and cost optimized

---

This layers infrastructure state is ensured using [Terraform](https://www.terraform.io/).  This project has the strong opinion that Terraform is the best tool to ensure the static immutable state of the infrastructure at the Service Layer.  A simple cron run by Ansible Tower, will every 20 minutes execute a `terraform plan` to verify the state of the infrastructure matches the Terraform state file.  With no reported changes the infrastructure is verified in the correct known state.  Any changes reported by Terraform would be an escalated Defcon level, requiring a human to intervene and manually update the state using `terraform apply`, ensuring the state is brought up the state expected in code.  See the Foundation Layer [README](https://github.com/SimplifyMyCloud/SMCInfrastructureState/tree/gcp_foundation/README.md) for coding standards and naming conventions along with requirements.

---

## Service Layer contents:
  - Helm Charts
  - Binary baked compute instances
  - Container baked instances


---

## Descriptions:

  - *Helm Charts*
    
    [Helm](https://helm.sh/) charts are used to deploy, and orchestrate, applications and services into Kubernetes.  Kubernetes will already be running as ensured by the Service Layer, and ready to accept Helm charts.  Other Kubernetes deployment methods can be used but this repo has the strong opinion on Helm.
  
  ---

  - *Binary baked compute instances*
    
    "Baked" refers to the process of using an automated build systems to snapshot the OS after the application binary has been installed and configured on the compute instance.  Once the instance is fully configured and ready to run in an environment, it is snapshotted, *aka baked*, and stored as a *immutable object* that can be deployed and booted, with a known and expected instance state that cannot, and will not, be changed once deployed to the environment.  All baked instances are versioned using [SemVer](https://semver.org/), any changes necessary to the baked instance, would require a bump in version number of the instance object.
  
  ---

  - *Container baked instances*
    
    A baked container instance is best practices when using a container optimized OS like [CoreOS](https://coreos.com/), [RancherOS](https://rancher.com/rancher-os/), or [Google Container Optimized OS](https://cloud.google.com/container-optimized-os/).  Since these OS's are typically read-only file systems, they are baked by default.  The only change that occurs is configuring which container to pull and run on the OS boot.


  
