Tags: [[Windows]] [[Definitions]] [[Cybersecurity]] #Active_Directory

## Definitions 
### **Active Directory**
- is a directory service for Windows enterprise environments that Microsoft officially released in 2000 with Windows Server 2000. Microsoft has been incrementally improving AD with the release of each new server OS version. Based on the protocols x.500 and LDAP that came before it (which are still utilized in some form today), AD is a distributed, hierarchical structure that allows centralized management of an organization's resources, including users, computers, groups, network devices and file shares, group policies, devices, and trusts. AD provides authentication, accounting, and authorization functionalities within a Windows enterprise environment. It also allows administrators to manage permissions and access to network resources.

 Active directory is the most used [IAM]([[Identity and Access Management]]) in the world 


**[[Domain]]** -  A group of objects that share the same AD database, such as users or devices. 

**[[Tree]]** - is one or more domains grouped. Think of this as the domains test.local, staging.test.local, and preprod.test.local, which will be in the same tree under test.local. Multiple trees can exist in this notion. 

**[[Forest]]** - Is a group of multiple trees. This is the topmost level, which is composed of all domains. 


**[[Organizational Units (OU)]]** - are Active Directory containers containing user groups, Computers, and other OUs.

**Trust** - can be defined as access between resources to gain permission/access to resources in another domain. 

**[[Domain Controller]]** - is (generally) the Admin of the Active Directory used to set up the entire Directory. The role of the Domain Controller is to provide Authentication and Authorization to different services and users. In Active Directory, the Domain Controller has the topmost priority and has the most authority/privileges.

**Active Directory Data Store** - contains Database files and processes that store and manages directory information for users, services, and applications. Active Directory Data Store contains the file NTDS.DIT, the most critical file within an AD environment; domain controllers store it in the %SystemRoot%\NTDS folder.




