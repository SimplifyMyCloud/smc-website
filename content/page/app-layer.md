---
title: App Layer
subtitle: Application and Service Orchestration
comments: false
---

## Description
---

*The goal of the App Layer is the orchestration of applications and services running on the Service Layer.*

---

The App Layer enables developers to experiment freely with new ideas, without asking for approval to deploy into running services in the dev environment.  It allows for developers to be confident the infrastructure they developed and tested against in the test environment is a clone of production.  It allows for developers to understand and feel confident in the production environment as its only accessible by automation and not humans.  The app layer also gives the operations team confidence that the applications being launched by developers are already wired into the infrastructure, allowing for deep inspection observbility, rich logging and monitoring for customer facing environments.  The App layer also protects the business from unplanned, shadow applications.

---

## App Layer enabling DevOps:
  - compassion for developers by providing freedom to tinker on already deployed services
  - compassion for operations by knowing that applications being deployed already been configured for logging, monitoring, observability, and right-sized 
  - compassion for sales by allowing for demo environments to be deployed with just access to [Ansible Tower](https://www.ansible.com/products/tower), and a few buttons clicked

---

This layers infrastructure state is ensured using [Ansible](https://www.ansible.com/).  This project has the strong opinion that Ansible is the best tool to orchestrate across the App Layer.  As Ansible can perform tasks the chain and perform them in order, Ansible is the perfect tool to deploy applications and services across the App Layer. See the App Layer [README](https://github.com/SimplifyMyCloud/SMCInfrastructureState/blob/gcp_app/AppLayer/README.md) for coding standards and naming conventions along with requirements.

---

## App Layer contents:
  - Helm Charts
  - Baked compute instances

---

## Descriptions:

  - *Helm Charts*
    
    [Helm](https://helm.sh/) charts are used to deploy, and orchestrate, applications and services into Kubernetes.  Kubernetes will already be running as ensured by the Service Layer, and ready to accept Helm charts.  Other Kubernetes deployment methods can be used but this repo has the strong opinion on Helm.

  - *Baked compute instances*

    Preconfigured off of production to allow for deploying static assets, baked instances provide a path to hosting applications that are not running in containers, or are running in containers but not optimized for Kubernetes and therefore need a one-to-one mapping of container to instance.
