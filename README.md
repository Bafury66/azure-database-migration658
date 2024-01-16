# Azure Database Migration Project
# Summary
### This is part of the AiCore Course - Cloud Engineer pathway. In this project, project manager would architect and implement a cloud-based database system on Microsoft Azure, showcasing author's hands-on expertise in cloud engineering.
# Project Prerequisites
### For this project, different services on Microsoft Azure are used, therefore a login credential which allows to create different resources on Azure is needed. Luckily since this is part of AiCore course, such info is provided.
### For those who want to try out this process themselves, an Azure account will be required. To sign up for an Azure account, use this link https://azure.microsoft.com/en-us/get-started/azure-portal/ or https://azure.microsoft.com/en-us/free/ for a limited free account.
# Set up the Production Environment
### Task 1 - Set up the Windows Virtual Machine
#### Window Virtual Machine (VM) can be set up in Azure portal with "Create a resource" button. 
### Task 2 - Connect to the Windows Virtual Machine
#### Connecting to the Windows VM is simple, we first need to download the RDP file from the *Connect* section, then open this RDP file using different clients on different OS.
#### These include 
- *Remote Desktop Connection* on Windows OS.
- *Microsoft Remote Desktop app* on MacOS.
- Client like *Remmina* for Linux OS.
### Task 3 - Install SQL Server and SQL Server Management Studio (SSMS)
### Task 4 - Create the Production Database 
#### The pproduction Database is created by by restoring it from this backup file https://aicore-portal-public-prod-307050600709.s3.eu-west-1.amazonaws.com/project-files/93dd5a0c-212d-48eb-ad51-df521a9b4e9c/AdventureWorks2022.bak
#### 

# Migrate to  Azure SQL Database
### Task 1 - Set up Azure SQL Database
Azure SQL database is required in this project, this serves as the target for migrating our on-premise database. This was created on Microsoft Azure together with a SQL database server both are under the same resource group.

Our SQL database server uses the *SQL Server Authentication* method where an user and password was created for login.

Since this is only a project to demonstrate database migration, the service and compute tier requirement is low, hence *Basic* service tier was selected to minimise the cost. 

After the creation of the databse, a connection test was performed with VSCode to ensure database is working properly. This requires

- SQL Server extension on VSCode is installed
- *Public network access* in server firewall has to set to *Selected networks*
- Azure login account has to be added onto VSCode
- Client IP address range (start IP and end IP) must be added to the firewall rule.

*Notice that when adding a new connection on VSCode, the database name must be the same as the one on Azure, otherwise the connection will fail. It is not optional.*

### Task 2 - Prepare for Migration
Here we use Microsoft's Azure Data Studio as the tool to manage the migration process. This piece of database management tool was installed on the VM created earlier and connected to on-premise database also set up on the VM.

### Task 3 - Connect to Azure SQL Database
Apart from the on-premise database, Azure Data Studio also used to connect to the newly created Azure database. With these two database connected to the same tool, schema comparison and data migration can be executed.

### Task 4 - Schema Migration
Before migrating the data, we need to process schema migration first. Luckily this can be done with *SQL Server Schema Compare* extension on Azure Data Stuido. In this project, this extension was used to compare the schema on the source (on-premise) database and target (Azure SQL) database. Schema migration was followed after comparison was done.

### Task 5 - Data Migration
TBCX XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

### Task 6 - Validate Migration Success
Database migration validation was carried out with manually compare a couple of top rows on three different tables, all rows checked were ok.

Also Microsoft Visual Studio was used to perform a more comprehensive validation by checking through every row of data on every table migrated and it turns out to be fine, too.
