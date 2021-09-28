---
layout:  post
title: Describe provisioning relational data services
---

### What is provisioning?
* **Provisioning** is the act of running series of tasks that a service provider, such as Azure SQL Database, performs to create and configure a service.
* specify parameters that determine the size of the resources required (how much disk space, memory, computing power, and network bandwidth).
* The act of increasing (or decreasing) the resources used by a service is called **scaling**.

#### Tools
* The Azure portal
* The Azure command-line interface (CLI)
* Azure PowerShell
* Azure Resource Manager templates

* Send the template to Azure using the az deployment group create command in the Azure CLI, 
or New-AzResourceGroupDeployment command in Azure PowerShell.
[Stpes for provisioning](https://docs.microsoft.com/en-us/learn/modules/explore-provision-deploy-relational-database-offerings-azure/4-describe-provision-postgresql-mysql)

### Configuring relational data services
* The default connectivity for Azure relational data services is to disable access to the world.
* To enable connectivity, use the Firewalls and virtual networks page for a service. 
* **Selected Networks : Virtual network, Firewall, and Exceptions**
* An Azure Virtual Network is a representation of your own network in the cloud. 
* In the **Virtual networks section**, you can specify which virtual networks are allowed to route traffic to the service.
* **Firewall section**, add the IP address of the computer.
* **Exceptions setting** allows you to enable access to any other services that cannot be uniquely isolated through virtual network or IP address rules.
* **Firewalls and virtual networks** page for an Azure SQL database.
* **Azure SQL Database communicates over port 1433**
* **PostgreSQL port number 5432**
*  **MySQl port number 3306**
* A firewall rule of 0.0.0.0 enables all Azure services to pass through the server-level firewall rule and attempt to connect to a single or pooled database through the server.
* **Azure Private Endpoint** is a network interface that connects you privately and securely to a service powered by Azure Private Link
* **The Private endpoint connections page** for a service allows you to specify which private endpoints, if any, are permitted access to your service. You can use the settings on this page, together with the 
* **Firewalls and virtual networks page**, to completely lock down users and applications from accessing public endpoints to connect to your Azure SQL Database account.

### Configure authentication
* With **Azure Active Directory (AD)** authentication ->centrally manage the identities of database users and other Microsoft services in one central location. 
* Central ID management provides a single place to manage database users and simplifies permission management.

### Configure access control
* Access control defines what a user or application can do with your resources once they've been authenticated.
* Azure role-based access control (Azure RBAC) helps you manage who has access to Azure resources, and what they can do with those resources. 
  * Allow one user to manage virtual machines in a subscription and another user to manage virtual networks.
  * Allow a database administrator group to manage SQL databases in a subscription.
  * Allow a user to manage all resources in a resource group, such as virtual machines, websites, and subnets.
  * Allow an application to access all resources in a resource group.

* **Roles**
   * Owner ->Full Access
   * Contributor -> create and manage but not grant
   * Reader -> View existing resources
   * User Access Administrator -> manage user access to Azure resources.
* A **scope** lists the set of resources that the access applies to. 
* Add role assignments to a resource in the Azure portal using the **Access control (IAM)** page.
* Add **role assignments** to a resource in the Azure portal using the Access control (IAM) page.

### Configure advanced data security
* Authentication
* Authorization
* Advanced data security implements threat protection and assessment.

[Describe configuring Azure SQL Database, Azure Database for PostgreSQL, and Azure Database for MySQL](https://docs.microsoft.com/en-us/learn/modules/explore-provision-deploy-relational-database-offerings-azure/6-configure-sql-database-mysql-postgresql)
* An **ACL** contains a list of resources, and the objects (users, computers, and applications) that are allowed to access those resources. 
* When an object attempts to use a resource that is protected by an ACL, if it's not in the list, it won't be given access.
* Items that implement network-based ACLs include routers and load balancers.
* Connection established
    Gateway (IP listening to port 1433) -> either redirects traffic to the database cluster, or acts as a proxy for the database cluster ->Inside the database cluster, traffic is forwarded to the appropriate Azure SQL database.
    


* 
