---
title: Foundation Layer
subtitle: Rock Solid, Static, and Secure Cloud Foundation
comments: false
---

## Description
---

*The goal of the Foundation Layer is to ensure the state and maintain the perimeter security of the cloud.*

The Foundation Layer is the bedrock of the cloud, ensuring a known and easily verifiable state of the security of the cloud.  All infrastructure lives in a git repo, enabling the Foundation Layer to be protected from single person decisions, enabling multiple git pull request approvers before any state change is allowed.  

- Foundation Layer Empathy:
  - dev empathy by providing at least two sets of eyes for any changes to firewalls
  - ops empathy by providing a known security state that cannot be changed with out ops approval on the pull request
  - business empathy by providing an always known and easily verifiable security state that cannot be changed without approval from each team, dev, ops and business


This layers infrastructure state is ensured using [Terraform](https://www.terraform.io/).  This project has the strong opinion that Terraform is the best tool to ensure the static immutable state of the infrastructure at the Service Layer.  A simple cron run by Ansible Tower, will every 20 minutes execute a `terraform plan` to verify the state of the infrastructure matches the Terraform state file.  With no reported changes the infrastructure is verified in the correct known state.  Any changes reported by Terraform would be an escalated Defcon level, requiring a human to intervene and manually update the state using `terraform apply`, ensuring the state is brought up the state expected in code.  See the Foundation Layer [README](https://github.com/SimplifyMyCloud/SMCInfrastructureState/tree/gcp_foundation/README.md) for coding standards and naming conventions along with requirements.

---

### Foundation Layer contents:
  - Networking
  - Security
  - Users and Access

---

### Descriptions:

  - *Networking*
    
    VPCs, subnets, routes, static IPs, all part of the overall network layout of Google Cloud and ensured into a state by the Foundation Layers.  In the old days of on-premise hosting, pushing a new build of the application did not require a re-flash and re-setup of the routers, switches and firewalls.  The Foundation Layer state shall remain static, rarely changed but constantly verified.  Making changes to the Foundation Layer in *any environment including DevEnv*, should be treated with respect and triple approved with input from development, operations, and the business.

---

  - *Security*
    
    Security of the cloud is paramount and the single most important piece of the business operating in the cloud.  Without security the customers, internal and external, cannot trust or rely on the services running in the cloud.  Security in the Foundation Layer consists mostly of the firewall rules, what is allowed in and out, who is allowed to connect to who, and to open the cloud to the internet.
  
---

  - *Users and Access*
    
    Google Cloud IAM - *Cloud Identity & Access Management*, is the process of vetting if a user has access and if they do what level of access using grouped sets of permissions into roles.
