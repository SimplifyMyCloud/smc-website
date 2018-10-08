#### Project Goal

The goal of this project is to provide an automation starting point for Google Cloud, AWS and Azure that focuses on simplicity, security and best practices on day one.  Also to enable an infrastructure culture that is compassionate about its customers and enables the business to do business and focus on the business.

---

#### Recommended Best Practices

Each architectural decision is based on current documentation from each cloud provider.  

---

#### Layers enabling DevOps

The infrastructure is split into 3 layers, the [Foundation layer](foundation-layer.html), the [Service layer](service-layer.html), and the [App layer](app-layer.html).  

Layering the infrastructure enables seperation of responsibilities , enabling a DevOps culture to flourish.

  - Foundation Layer:
    - Allows for higher security settings for the Foundation layer to be enforced, protecting the business from unknown open ports or unauthorized logins.

  - Service Layer:
    - Allows for operations to wire up logging, monitoring, and observability into the services required to deploy applications.
    
  - App Layer:
    - Allows for developers to have the freedom to tinker with ideas in the development environment while knowing that the apps running in production are identical to what they intended to ship.

---

#### Deliverable Timeline:

  - Google Cloud Dec 2018 ~ [Github Repo](https://github.com/SimplifyMyCloud/GCP-InfrastructureState "GCP SMC Github repo")

  - AWS October 2018 ~ [Github Repo](https://github.com/SimplifyMyCloud/AWS-InfrastructureState "AWS SMC Github repo")

  - Azure 2019 ~ [Github Repo](https://github.com/SimplifyMyCloud/Azure-InfrastructureState "Azure SMC Github repo")