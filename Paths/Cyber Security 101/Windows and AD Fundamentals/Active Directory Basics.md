Link : https://tryhackme.com/room/winadbasics

This room will introduce the basic concepts and functionality provided by Active Directory.


![image](https://github.com/user-attachments/assets/dba9cc75-1867-43fe-8d0d-5020b6b33c01)


**Module 1: Introduction**

Microsoft's Active Directory is the backbone of the corporate world. It simplifies the management of devices and users within a corporate environment. In this room, we'll take a deep dive into the essential components of Active Directory.

Room Objectives

In this room, we will learn about Active Directory and will become familiar with the following topics

1. What Active Directory is
   
2. What an Active Directory Domain is
   
3. What components go into an Active Directory Domain
   
4. Forests and Domain Trust
   
5. And much more!
   
Room Prerequisites

General familiarity with Windows. Check the Windows Fundamentals module for more information on this.

**Answer the questions below**

Click and continue learning!

Answer: No Answer required

**Module 2: Windows Domains**

Picture yourself administering a small business network with only five computers and five employees. In such a tiny network, you will probably be able to configure each computer separately without a problem. You will manually log into each computer, create users for whoever will use them, and make specific configurations for each employee's accounts. If a user's computer stops working, you will probably go to their place and fix the computer on-site.

While this sounds like a very relaxed lifestyle, let's suppose your business suddenly grows and now has 157 computers and 320 different users located across four different offices. Would you still be able to manage each computer as a separate entity, manually configure policies for each of the users across the network and provide on-site support for everyone? The answer is most likely no.

To overcome these limitations, we can use a Windows domain. Simply put, a Windows domain is a group of users and computers under the administration of a given business. The main idea behind a domain is to centralise the administration of common components of a Windows computer network in a single repository called Active Directory (AD). The server that runs the Active Directory services is known as a Domain Controller (DC).

![image](https://github.com/user-attachments/assets/6edb5d4a-5bf8-4183-aa87-d45d97dc317d)

The main advantages of having a configured Windows domain are:

Centralised identity management: All users across the network can be configured from Active Directory with minimum effort.

Managing security policies: You can configure security policies directly from Active Directory and apply them to users and computers across the network as needed.

A Real-World Example

If this sounds a bit confusing, chances are that you have already interacted with a Windows domain at some point in your school, university or work.

In school/university networks, you will often be provided with a username and password that you can use on any of the computers available on campus. Your credentials are valid for all machines because whenever you input them on a machine, it will forward the authentication process back to the Active Directory, where your credentials will be checked. Thanks to Active Directory, your credentials don't need to exist in each machine and are available throughout the network.

Active Directory is also the component that allows your school/university to restrict you from accessing the control panel on your school/university machines. Policies will usually be deployed throughout the network so that you don't have administrative privileges over those computers.

**Welcome to THM Inc.**

During this task, we'll assume the role of the new IT admin at THM Inc. As our first task, we have been asked to review the current domain "THM.local" and do some additional configurations. You will have administrative credentials over a pre-configured Domain Controller (DC) to do the tasks.

Should you prefer to connect to it via RDP, you can use the following credentials:

Username: Administrator

Password: Password321

Note: When connecting via RDP, use THM\Administrator as the username to specify you want to log in using the user Administrator on the THM domain.

Since we will be connecting to the target machine via RDP, this is also a good time to start the AttackBox (unless you are using your own machine).

**Answer the questions below**

In a Windows domain, credentials are stored in a centralised repository called...

Answer: `Active Directory`

The server in charge of running the Active Directory services is called...

Answer: `Domain Controller`

**Module 3: Active Directory**

﻿The core of any Windows Domain is the Active Directory Domain Service (AD DS). This service acts as a catalogue that holds the information of all of the "objects" that exist on your network. Amongst the many objects supported by AD, we have users, groups, machines, printers, shares and many others. Let's look at some of them:

**Users**

Users are one of the most common object types in Active Directory. Users are one of the objects known as security principals, meaning that they can be authenticated by the domain and can be assigned privileges over resources like files or printers. You could say that a security principal is an object that can act upon resources in the network.

Users can be used to represent two types of entities:

1. People: users will generally represent persons in your organisation that need to access the network, like employees.

2. Services: you can also define users to be used by services like IIS or MSSQL. Every single service requires a user to run, but service users are different from regular users as they will only have the privileges needed to run their specific service.


**Machines**

Machines are another type of object within Active Directory; for every computer that joins the Active Directory domain, a machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

The machine accounts themselves are local administrators on the assigned computer, they are generally not supposed to be accessed by anyone except the computer itself, but as with any other account, if you have the password, you can use it to log in.

Note: Machine Account passwords are automatically rotated out and are generally comprised of 120 random characters.

Identifying machine accounts is relatively easy. They follow a specific naming scheme. The machine account name is the computer's name followed by a dollar sign. For example, a machine named DC01 will have a machine account called `DC01$`.

**Security Groups**

If you are familiar with Windows, you probably know that you can define user groups to assign access rights to files or other resources to entire groups instead of single users. This allows for better manageability as you can add users to an existing group, and they will automatically inherit all of the group's privileges. Security groups are also considered security principals and, therefore, can have privileges over resources on the network.

Groups can have both users and machines as members. If needed, groups can include other groups as well.

Several groups are created by default in a domain that can be used to grant specific privileges to users. As an example, here are some of the most important groups in a domain:

Security Group	             |           Description
                  
Domain Admins	               =>           Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs.
                             
Server Operators	           =>           Users in this group can administer Domain Controllers. They cannot change any administrative group memberships.
                             
Backup Operators	           =>           Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers.
                             
Account Operators	           =>           Users in this group can create or modify other accounts in the domain.

Domain Users	               =>           Includes all existing user accounts in the domain.

Domain Computers	           =>           Includes all existing computers in the domain.

Domain Controllers	         =>           Includes all existing DCs on the domain.

You can obtain the complete list of default security groups from the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups).

**Active Directory Users and Computers**

To configure users, groups or machines in Active Directory, we need to log in to the Domain Controller and run "Active Directory Users and Computers" from the start menu:

![image](https://github.com/user-attachments/assets/5a5ff8b5-ec97-445b-8ccb-cffe29adaa4e)

This will open up a window where you can see the hierarchy of users, computers and groups that exist in the domain. These objects are organised in Organizational Units (OUs) which are container objects that allow you to classify users and machines. OUs are mainly used to define sets of users with similar policing requirements. The people in the Sales department of your organisation are likely to have a different set of policies applied than the people in IT, for example. Keep in mind that a user can only be a part of a single OU at a time.

Checking our machine, we can see that there is already an OU called THM with four child OUs for the IT, Management, Marketing and Sales departments. It is very typical to see the OUs mimic the business' structure, as it allows for efficiently deploying baseline policies that apply to entire departments. Remember that while this would be the expected model most of the time, you can define OUs arbitrarily. Feel free to right-click the THM OU and create a new OU under it called Students just for the fun of it.

![image](https://github.com/user-attachments/assets/276bdd44-7c76-4e4c-aa2b-1fa136ada2f6)


If you open any OUs, you can see the users they contain and perform simple tasks like creating, deleting or modifying them as needed. You can also reset passwords if needed (pretty useful for the helpdesk):

![image](https://github.com/user-attachments/assets/641ff7fc-872b-4975-bd3c-0204bd270a66)

You probably noticed already that there are other default containers apart from the THM OU. These containers are created by Windows automatically and contain the following:

1. Builtin: Contains default groups available to any Windows host.

2. Computers: Any machine joining the network will be put here by default. You can move them if needed.

3. Domain Controllers: Default OU that contains the DCs in your network.

4. Users: Default users and groups that apply to a domain-wide context.

5. Managed Service Accounts: Holds accounts used by services in your Windows domain.

**Security Groups vs OUs**

You are probably wondering why we have both groups and OUs. While both are used to classify users and computers, their purposes are entirely different:

OUs are handy for applying policies to users and computers, which include specific configurations that pertain to sets of users depending on their particular role in the enterprise. Remember, a user can only be a member of a single OU at a time, as it wouldn't make sense to try to apply two different sets of policies to a single user.

Security Groups, on the other hand, are used to grant permissions over resources. For example, you will use groups if you want to allow some users to access a shared folder or network printer. A user can be a part of many groups, which is needed to grant access to multiple resources.


**Answer the questions below**

Which group normally administrates all computers and resources in a domain?

Answer: `Domain Admins`

What would be the name of the machine account associated with a machine named TOM-PC?

Answer: `TOM-PC$`

Suppose our company creates a new department for Quality Assurance. What type of containers should we use to group all Quality Assurance users so that policies can be applied consistently to them?

Answer: `Organizational Units`

**Module 4: Managing Users in AD**

Your first task as the new domain administrator is to check the existing AD OUs and users, as some recent changes have happened to the business. You have been given the following organisational chart and are expected to make changes to the AD to match it:

![image](https://github.com/user-attachments/assets/871df91e-fee7-4d07-aa48-0b83bcf8a3bb)

**Deleting extra OUs and users**

The first thing you should notice is that there is an additional department OU in your current AD configuration that doesn't appear in the chart. We've been told it was closed due to budget cuts and should be removed from the domain. If you try to right-click and delete the OU, you will get the following error:

![image](https://github.com/user-attachments/assets/ea18ae31-90d3-412e-b88e-473bb2f69880)

By default, OUs are protected against accidental deletion. To delete the OU, we need to enable the Advanced Features in the View menu:

![image](https://github.com/user-attachments/assets/c20c3cc0-d010-4329-9d62-1923f85257d3)

This will show you some additional containers and enable you to disable the accidental deletion protection. To do so, right-click the OU and go to Properties. You will find a checkbox in the Object tab to disable the protection:

![image](https://github.com/user-attachments/assets/0c5038ce-a835-4cfa-a0eb-a0cfe8a1aaf2)

Be sure to uncheck the box and try deleting the OU again. You will be prompted to confirm that you want to delete the OU, and as a result, any users, groups or OUs under it will also be deleted.

After deleting the extra OU, you should notice that for some of the departments, the users in the AD don't match the ones in our organisational chart. Create and delete users as needed to match them.

**Delegation**

One of the nice things you can do in AD is to give specific users some control over some OUs. This process is known as delegation and allows you to grant users specific privileges to perform advanced tasks on OUs without needing a Domain Administrator to step in.

One of the most common use cases for this is granting IT support the privileges to reset other low-privilege users' passwords. According to our organisational chart, Phillip is in charge of IT support, so we'd probably want to delegate the control of resetting passwords over the Sales, Marketing and Management OUs to him.

For this example, we will delegate control over the Sales OU to Phillip. To delegate control over an OU, you can right-click it and select Delegate Control:

![image](https://github.com/user-attachments/assets/d0fbcefd-1e07-47d2-8828-8a85d246a376)

This should open a new window where you will first be asked for the users to whom you want to delegate control:

Note: To avoid mistyping the user's name, write "phillip" and click the Check Names button. Windows will autocomplete the user for you.

![image](https://github.com/user-attachments/assets/6ffb5795-1144-4f52-9da1-efd779cebf17)

Click OK, and on the next step, select the following option:

![image](https://github.com/user-attachments/assets/f0fdf08a-0724-4458-a728-42d8477ccdc0)

Click next a couple of times, and now Phillip should be able to reset passwords for any user in the sales department. While you'd probably want to repeat these steps to delegate the password resets of the Marketing and Management departments, we'll leave it here for this task. You are free to continue to configure the rest of the OUs if you so desire.

Now let's use Phillip's account to try and reset Sophie's password. Here are Phillip's credentials for you to log in via RDP:

Username: phillip

Password: Claire2008

Note: When connecting via RDP, use THM\phillip as the username to specify you want to log in using the user phillip on the THM domain.

While you may be tempted to go to Active Directory Users and Computers to try and test Phillip's new powers, he doesn't really have the privileges to open it, so you'll have to use other methods to do password resets. In this case, we will be using Powershell to do so:

Windows PowerShell (As Phillip)
```
PS C:\Users\phillip> Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

New Password: *********

VERBOSE: Performing the operation "Set-ADAccountPassword" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".
```
Since we wouldn't want Sophie to keep on using a password we know, we can also force a password reset at the next logon with the following command:

Windows PowerShell (as Phillip)

```
PS C:\Users\phillip> Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose

VERBOSE: Performing the operation "Set" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".
```

Log into Sophie's account with your new password and retrieve a flag from Sophie's desktop.

In the Target Machine delegate the user Philip for Reset Password (Follow steps of `delegation` from above)

Type  `remmina` in terminal on local machine

![image (3)](https://github.com/user-attachments/assets/bf819334-c0ef-4c81-a01e-607786cca6a6)

Now in the `remmina` dashboard, enter the IP Address of the target machine

![Screenshot from 2025-06-26 18-09-27](https://github.com/user-attachments/assets/3b31b283-857c-469e-8dc3-e3e351e88f84)

We will see a dialog box requesting the Username and Password. Here we enter the credentials of Phillip

![Screenshot from 2025-06-26 18-11-59](https://github.com/user-attachments/assets/a31f5bc6-a235-4678-9fbf-872b6446a860)
![phillip](https://github.com/user-attachments/assets/e0009e9a-b25a-4070-aaef-3d07e39439bc)

And now we are in Phillip's system, we try to open Powershell

![p-home](https://github.com/user-attachments/assets/344817d2-a1f4-4766-9b8a-61f1d4dbe830)

![pwshll](https://github.com/user-attachments/assets/d7f8f6e7-c767-47e0-a070-46e20692492d)

And now we use the commnad for resetting the password the user `Sophie`

`Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt ‘New Password’) -Verbose`

![cmd](https://github.com/user-attachments/assets/9020ef79-2f65-4708-a0d1-9e2e10e4e8bc)

We will be prompted to enter a new password after clicking on enter after this command and there we will enter a new password and if the password meets the criteria then we will see something like this

![success](https://github.com/user-attachments/assets/08080a75-5aa3-4155-bd57-e262cc3921cb)

Now we use `remmina` again and we use sophie credentials and password should be the password we set earlier 

![sophie](https://github.com/user-attachments/assets/c7fd9b8a-fcd5-40c9-9c37-e9da97def146)

And we will be in sophie's home screen there we will find a flag

![sophie-home](https://github.com/user-attachments/assets/e39659ba-55b2-4bac-b3a8-47bef3804c1b)

![flag](https://github.com/user-attachments/assets/5f3bccf3-4ddc-461d-b8cb-0539548ee2e4)

**Answer the questions below**

What was the flag found on Sophie's desktop?

Answer: `THM{thanks_for_contacting_support}`

The process of granting privileges to a user over some OU or other AD Object is called...

Answer: `delegation`

**Module 5: Managing Computers in AD**

By default, all the machines that join a domain (except for the DCs) will be put in the container called "Computers". If we check our DC, we will see that some devices are already there:

![image](https://github.com/user-attachments/assets/34ce99d1-138a-4eb5-8dcb-5e2936649d7c)

We can see some servers, some laptops and some PCs corresponding to the users in our network. Having all of our devices there is not the best idea since it's very likely that you want different policies for your servers and the machines that regular users use on a daily basis.

While there is no golden rule on how to organise your machines, an excellent starting point is segregating devices according to their use. In general, you'd expect to see devices divided into at least the three following categories:

1. Workstations

Workstations are one of the most common devices within an Active Directory domain. Each user in the domain will likely be logging into a workstation. This is the device they will use to do their work or normal browsing activities. These devices should never have a privileged user signed into them.

2. Servers

Servers are the second most common device within an Active Directory domain. Servers are generally used to provide services to users or other servers.

3. Domain Controllers

Domain Controllers are the third most common device within an Active Directory domain. Domain Controllers allow you to manage the Active Directory Domain. These devices are often deemed the most sensitive devices within the network as they contain hashed passwords for all user accounts within the environment.

Since we are tidying up our AD, let's create two separate OUs for Workstations and Servers (Domain Controllers are already in an OU created by Windows). We will be creating them directly under the thm.local domain container. In the end, you should have the following OU structure:

![image](https://github.com/user-attachments/assets/18ea75c5-0966-4e69-a921-5bc8a8549845)

Now, move the personal computers and laptops to the Workstations OU and the servers to the Servers OU from the Computers container. Doing so will allow us to configure policies for each OU later.

First let's create two OU's naming them `Workstations` and `Servers`

![OU](https://github.com/user-attachments/assets/8f8dce75-e982-4b9e-9016-9343a7e9d80c)

![Workstations](https://github.com/user-attachments/assets/88e563f5-b547-4591-874d-5c79bfe9fbe6) 
![Servers](https://github.com/user-attachments/assets/d011db7d-cb9e-4e19-9552-438db8c56c92)

And now we go the Container called `Computer` in `thm.local` and we find some servers, PCs and laptops

Our task is to move PCs and Laptops to the OU `Workstations` 

![Move1](https://github.com/user-attachments/assets/9ffdcde7-3997-4615-af6c-081b51061819)

![Move2](https://github.com/user-attachments/assets/7238bf2d-b424-4567-b9b5-9fc17248df21)

and we move Servers to the OU `Servers`

![Move3](https://github.com/user-attachments/assets/1da5f490-550e-47c8-ba2b-0c35d83d2cc9)

![Move4](https://github.com/user-attachments/assets/75065dae-6318-4132-9339-b11e8c50d799)

And in `Workstations` OU we find 7 available computers and that is the answer to the above question

![Moved](https://github.com/user-attachments/assets/93bb598d-7308-4db8-855b-02deb60b2650)

**Answer the questions below**

After organising the available computers, how many ended up in the Workstations OU?

Answer : `7`

Is it recommendable to create separate OUs for Servers and Workstations? (yay/nay)

Answer: `yay`

