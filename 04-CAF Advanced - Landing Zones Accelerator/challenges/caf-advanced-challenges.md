# CAF Hackathon Advanced - Azure Landing Zones Accelerator

---

## Challenge 1 - Azure landing zone conceptual architecture deployment

In this challenge you will be deploying one of the Reference implementations located in this [repository](https://github.com/Azure/Enterprise-Scale).

Success criteria for this challenge:

- Plan and document the IP addressing for the Hub network. Customer will be leveraging at least Azure Firewall, Azure VPN Gateway, and Azure Bastion.
- In your plan, clearly document subnet names, whether the use of NSGs and / or UDRs is allowed, and the minimum recommended subnet size. Inlcude references to online documentation.
- Create a high-level deployment workflow (diagram not a CICD pipeline!) including pre-requisites.
- Deploy either the Trey Research or AdventureWorks reference implementation.

- **Do not deploy** the integrated CICD pipeline

---

## Challenge 2 - IaC with GitHub Actions

In this challenge you will be manually creating a CICD pipeline which will allow you to operate the Azure platform using [AzOps](https://github.com/Azure/AzOps) (IaC with GitHub Actions).

This PowerShell module is rooted in the principle that everything in Azure is a resource and to operate at-scale, it should be managed declaratively to determine target goal state of the overall platform. Guidance for this challenge is located [here](https://github.com/azure/azops/wiki/github-actions).

Success criteria for this challenge:

- Configure AzOps via Portal or command-line script
- Initiate the first Pull workflow
- Validate AzOps by creating a new [Policy Assignment](https://github.com/Azure/Enterprise-Scale/wiki/Deploying-Enterprise-Scale-Platform-DevOps#create-new-policy-assignment-for-validation)

## Challenge 2a - PaC with GitHub Actions

In this challenge you will be using Policy-As-Code to modify a policy definition which is blocking you from creating the Azure Bastion Subnet.

- In your hub network, try to create the Azure Bastion Subnet. Azure Policy should block the operation.
- Modify the policy which is enforcing the use of Network Security Groups. You are not allowed to change the policy effect. A deny is a deny.
- Create the Azure Bastion Subnet.

---

## Challenge 3 - Azure VM BCDR at scale

In this challenge you will be deploying an Azure Virtual Machine in the same region as your Hub network which will be auto-enabled for backup and DR on creation using Azure Policy. Explore the possibility of using tags to associate backup and DR policies via Azure Policy.

Success criteria for this challenge:

- Configure Azure Backup (e.g., vault, backup policy, etc.)
- Configure Azure Policy to auto-enable backup on VM creation
- Configure Azure Site Recovery (e.g., vault, policy, etc.)
- Configure Azure Policy to auto-enable DR on VM creation
- Deploy VM
- Observer Azure Policy behaviour

---

## Challenge 4 - Governance Reporting

In this challenge you will be implementing [AzGovViz](https://github.com/JulianHayward/Azure-MG-Sub-Governance-Reporting) which is a PowerShell based script that iterates your Azure Tenant´s Management Group hierarchy down to Subscription level. It captures most relevant Azure governance capabilities such as Azure Policy, RBAC and Blueprints and a lot more. From the collected data AzGovViz provides visibility on your HierarchyMap, creates a TenantSummary, creates DefinitionInsights and builds granular ScopeInsights on Management Groups and Subscriptions.

Success criteria for this challenge:

- Setup AzGovViz from the console or GitHub Codespaces
- Run AzGovViz, show and tell your findings to your coach.
- Vist AzAdvertizer, show and tell your findings to your coach.

---

## Challenge 5 - Azure Design Review

In this challenge you will be doing an Azure design review to double-check that best practices are being followed. You will be using this [repo](https://github.com/Azure/review-checklists) which contains code and examples to operationalize spreadsheet-based checklists that can be used for Azure design reviews on multiple technologies.

Success criteria for this challenge:

- Use the Excel spreadsheet, import the latest checklist, and explore the contents of the file.
- If there is enough time left, use the Azure Resource Graph to verify your Azure environment.

---

## Challenge 6 - Azure Environment Clean-up

Works-in-progress
