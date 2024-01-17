## Terraform vs. Bash for Infrastructure Management on OVH Cloud/OpenStack Environment

**OpenStack via Terraform**    

**PROS:**    
From my perspective, the declarative syntax of Terraform makes it easy to define and manage infrastructure resources. As a user,
I can express the desired state of the infrastructure in a simple and readable format, reducing the need to deeply 
understand the underlying details of using the OpenStack CLI. OVH Cloud provides an official provider for services based 
on OpenStack, minimizing compatibility issues. Additionally, Terraform is not limited to OVH Cloud; in contrast to their 
OpenStack API, it makes it easier to plan and provision cross-cloud infrastructure (e.g., using OVH Cloud and AWS's Route 
53 for www-workload tasks). Another advantage of using OpenStack via Terraform during the www-workload task was the ability 
to track changes and preview the infrastructure before applying it using the planning feature.

The Terraform configuration can be easily stored in version control systems, enabling better collaboration. Its state file 
keeps track of the current state of the infrastructure, allowing easier updates to already running configurations compared 
to Bash scripts, which might require additional efforts to manage the state of the infrastructure. Using pre-created providers 
and modules reduces the amount of time required for creating custom scripts. The error-handling mechanism of Terraform, 
which checks the configuration before it's applied, reduces the chance of unexpected issues during provisioning, giving 
the opportunity to fix them during the planning stage. The planning stage allows the user to determine the order of resource
creation and their dependencies.

**CONS:**    
Having no prior knowledge or understanding of Terraform's concepts (providers, resources, etc.) would have required 
additional effort and increased my learning curve during the given task, as it necessitates understanding both tools. 
Another important point is that the official Terraform provider for OVH Cloud/OpenStack may not cover all the cloud's 
resources, potentially requiring the use of other methods to achieve specific goals.

**OpenStack via Bash**    

**PROS:**   
Bash scripts offer complete flexibility for achieving the desired outcome, enabling precise scripting and automation of 
provisioning tasks. These scripts provide full control over API calls and interactions with the OpenStack API, which is 
beneficial for creating complex and customized infrastructures. Unlike Terraform, Bash scripts do not require learning 
an additional tool but do demand a good understanding of scripting. With that knowledge, users can easily start using 
OpenStack on OVH Cloud. Bash scripts can be seamlessly integrated with other command-line tools and scripts, allowing the
creation of complex workflows and connecting OpenStack provisioning with other parts of the infrastructure.

**CONS:**    

There is a steep learning curve associated with using Bash scripting with OpenStack, requiring a deep understanding of 
both Bash and the OpenStack API. This complexity, compared to Terraform, would extend the time needed to complete tasks 
due to the more intricate configuration and longer, harder-to-understand command lines. Without the high-level abstraction 
provided by Terraform, Bash scripting can result in more error-prone code, especially when lacking the planning option 
that Terraform offers. Bash scripts would require more modifications and customization when adapting them to different 
scenarios, unlike Terraform, which allows for the separation of different parts of the infrastructure script for later 
reuse with minimal or no modifications. Lastly, maintaining and debugging Bash scripts may demand significant efforts, 
potentially leading to troubleshooting complexity, unlike Terraform scripts, which can be easily validated.

In summary, Bash scripts offer flexibility, but Terraform provides a more structured and efficient approach to managing 
infrastructure, especially if version control, state management, or collaboration are required. Terraform allows the user 
to destroy the entire infrastructure, reducing the risk of missing a running resource and incurring future costs.