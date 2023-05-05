## What is IaC


![image](https://user-images.githubusercontent.com/129324316/236433024-73b1dbfd-4f5a-4995-8dee-2845a9bd53ad.png)

Infrastructure as Code (IaC) is the managing and provisioning of infrastructure through code instead of through manual processes.

Cnfiguration files are created that contain our infrastructure specifications, which makes it easier to edit and distribute configurations. It also ensures that we provision the same environment every time.



## Benefits 

- Cost reduction
- Fast deployments
- Consistency in infrastructure
- Eliminating configuration drift.
- Reduce errors.


IaC generally Consists of 2 Parts:

- Configuration Management:
 Help to configure and test mach9ines to a specific state.
 Tools used - Ansible, Puppet, Chef
- Orchestration:
Helps to set up the architectures and networks rather than the configuration of individual machines.
Tools used - Terraform, Ansible

## Use Case

- Cloud deployments. IT pros manage and deploy cloud resources and configurations through template files, typically written in JSON. These files are particularly useful for hybrid-cloud organizations because they enable admins to manage multiple cloud environments with a single configuration or resource template.

- Infrastructure testing. With infrastructure as code, IT organizations can create a test environment that exactly replicates their production environment. This templated and fully functional mirror enables staff to freely test and experiment with features, updates and changes.

- Monitoring. Monitoring goes hand-in-hand with testing as a DevOps use case for IaC. The testing stage is all about experimentation, gathering information and assessing results, so monitoring is an intrinsic necessity. But infrastructure as code monitoring isn't limited to just testing.

## Configuration Management

Configuration management refers to the process by which all environments hosting software are configured and maintained. It is the process of maintaining systems, such as computer hardware and software, in a desired state. Configuration Management (CM) is also a method of ensuring that systems perform in a manner consistent with expectations over time.

## What is Ansible 

Ansible is an open source IT automation tool that automates provisioning, configuration management, application deployment, orchestration, and many other manual IT processes. We can use Ansible automation to install software, automate daily tasks, provision infrastructure and share automation across the entire organization.

![image](https://user-images.githubusercontent.com/129324316/236434882-4712c854-2bcc-4776-8e43-189825f909e0.png)


## Benefits of Ansible

- Ansible is agentless because we only need to install ansible on the controller, this method also makes the connection simple.
- It uses YAML. It is very powerful, but at the same time, very easy to learn.

## Use Cases of Ansible

- Provisioning: Provisioning is creating new infrastructure. 
- Continuous Delivery: Ansible provides a simpler way to automatically deploy applications. 
- Application Deployment: Ansible provides a simpler way to deploy applications across the infrastructure. 
- Ansible for Cloud Computing: Ansible makes it easy to provision instances across all cloud providers



