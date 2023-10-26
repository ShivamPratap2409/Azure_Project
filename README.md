# Azure_Project
**Project Summary:** 
when new file is add to 'BLOB' it will transfer that file to 'FILE SHARE' and get an EMAIL with the CONTENT of the File and also get SMS on PHONE that 'new file is added' and using Storage Sync Service the on premise Client can view the same file which is added to blob.

You can use the resoure group Templete and open azure service called Custom templete and upload this project there
Resource Group Of My Project: https://drive.google.com/file/d/1OEk62gZQLex6W1k6MdAKY9_5DNwjKz45/view


YOUTUBE VIDEO LINK OF PROJECT: https://www.youtube.com/watch?v=Mbb_aJYeyjI

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Overview**
So, there's a client who wants to access the internet and enter the Azure portal. When they add a blob file, a trigger will be activated in a Logic App. The Logic App will then transfer the file to Azure File Storage so that the on-premises server can also access the files added in the blob. To establish this real-time file synchronization, Azure Storage Sync Services are used to connect the on-premises server and Azure File share unidirectionally.
After the blob content is transferred to the file share, the Logic App calls an API, which sends an email notifying the content that was added or modified. Additionally, a third-party service called Twilio is used to send an SMS to the client's phone indicating that a new blob file has been added.
To create the on-premises environment, Azure Infrastructure as a Service (IaaS) is employed, utilizing a virtual machine (VM) within a subnet of a virtual network. Another subnet in the same virtual network holds a firewall. Incoming public requests first pass through the firewall, which only allows entry to the virtual network if firewall rules are satisfied. The virtual machine is connected to the firewall.
Inside the virtual machine, Azure Storage Sync Services files are installed to establish a connection with Azure File Share. A new disk driver is attached to the PC folder for this purpose. Additionally, Azure Monitor alerts are set up to trigger a warning alert when CPU usage exceeds 50%.

PDF File With ScreenShoots and explanation about project.
[Azure Project for Logic App By shivam.pdf](https://github.com/ShivamPratap2409/Azure_Project/files/13162108/Azure.Project.for.Logic.App.By.shivam.pdf)

Doc File of same PDF
[Azure Project.docx](https://github.com/ShivamPratap2409/Azure_Project/files/13162111/Azure.Project.docx)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




Flow Chat of Project: (__used Figma to create this Flow chat__)
![flow-1](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/7392ff3a-1511-4b1d-946f-010fe8d48065)




**Flow chat explanation** 

1.	Client will use internet to access the Azure Portal.

2.	Client will Add content to azure Blob storage. 

3.	A trigger will get activated in Azure Logic App (when new file is Added or Modified)
Inside Logic App we will make List of Blob 
And then we will create a for Each condition, so that when n number of Blob is added then it will take all the content.
Then we will take the content of blob and transfer them to new File share 

4.	All the content of blob gets transferred to file share. 
Then we will get log in to outlook inside the Logic App and we will then write How should we get an Email to our email address
We also login to Twilio a 3rd party service which is used to send the SMS on phone number. 
So will open the website of Twilio and signup and create account and then Buy a Number and the come to Home page of website we will get ID and token number we will copy it to our azure portal Logic App and create the Api connection between the Twilio and Azure and then we will right the Number to whom we have to send messages and messages will be send to that phone number after all the action of logic app completed successful 

5.	Client will get the Email and SMS 

6.	Azure file share is connected to On-premises and for doing so we have used a service in azure portal and installed that same service in on-premises computer (Azure storage sync)

7.	The on-premises have v-net and inside the v-net we have 2 subnets we have use Class A IP4 to give IP to subnets.
One subnet is only for firewall and other subnet is for Vm1 so when VM1 what to communicate on internet or with other V-net all the content goes through firewall and if it satisfies the condition of firewall then only allow to send the packets of data.

8.	It is connection between the Firewall and Vm1 

9.	The client will get the email. 

10.	Since there is connection between on-premises and azure storage using azure storage sync the client can file the modified or newly added file on real time and they can also add the files or modify the files, but the connection is unidirectional.

11.	Inside the Vm1 we have a monitoring service called Alert and condition is created that when CPU usage is more than 50% then I should get a warning message that usage of CPU is increased.

12.	I have also used LOCK in Vm1. By creating lock on VM1 no one can delete the VM1 unless and until file is deleted so nobody will by mistakenly delete the Vm1.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Services Used** 

1. Logic App
Azure Logic App is a Microsoft cloud-based service that provides a visual way to create and execute workflows and integrations between different systems and services. It allows you to automate business processes, workflows, and data integrations across various applications, services, and platforms. Logic Apps are built using a graphical designer, where you can define a series of steps and actions, known as triggers and connectors, to achieve a desired outcome.

2. Azure Blob Storage
Azure Blob Storage is a cloud-based object storage service provided by Microsoft Azure. It offers a scalable and secure solution for storing vast amounts of unstructured data, such as images, videos, documents, logs, and any other type of file.

3. Azure File Share
Azure File Share is a cloud-based file storage service provided by Microsoft Azure. It allows you to create and manage network file shares that can be accessible from multiple virtual machines (VMs) or other Azure services.

4. Azure Storage Sync Services
Provide synchronization of files and folders between on-premises servers and Azure storage. It allows you to replicate data between your local file servers and Azure File Shares or Azure Blob storage.

5. Virtual Networks
A virtual network acts as a logically isolated network within a public cloud environment, allowing you to provision and manage your own virtual network configuration.

6. Virtual Machine
It’s a physical computer system, with its own operating system and applications running on it. It enables users to run multiple independent instances of a computer system on a single physical machine or across multiple physical machines.

7. Firewall
Azure Firewall is a cloud-based network security service provided by Microsoft Azure. It acts as a centralized firewall solution for protecting virtual networks in Azure. Azure Firewall allows you to create and enforce network and application-level access control policies to secure your Azure resources. 

8. Monitor-Alerts
Monitor Alerts is a service provided by Microsoft Azure that helps you monitor and respond to changes in your Azure resources. It allows you to set up proactive notifications and automated actions based on metric values, log search queries, and various other conditions.

9. Twilio (3rd party)
Twilio is a cloud communications platform that enables businesses to easily integrate messaging, voice, and video capabilities into their applications. It provides a set of APIs and tools that developers can use to build and manage communication features in their software applications.

____________________________________________________________________________________________________________________________________________________________________________________

![Screenshot (75)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/fd950ab4-000a-499f-b64f-02c33a35fd8c)
![Screenshot (74)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ffc112a4-e342-4896-8389-aa41f425d528)
![Screenshot (73)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/1df05315-05db-47fe-aa24-87042104861c)
![Screenshot (72)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/2a9995ee-7f50-4ffd-8a41-c043c0059354)
![Screenshot (71)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/0a7a5ca7-3a8a-4384-8bc8-bc309d58b059)
![Screenshot (70)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ac4d1eea-a8db-4ab8-8a68-5af959443d6e)
![Screenshot (69)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/420cbac1-7a96-41a4-9952-61a90e47df04)
![Screenshot (4)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/56e04d12-8cbf-4d5e-8502-d59e6d7b5ea6)
![Screenshot (3)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/a969b32c-cf5e-4c55-8011-81eb25e96905)
![Screenshot (2)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/f844455c-e5e7-45a3-8a90-a67c3c09d0b7)
![Screenshot (1)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/cabacd7d-f14e-4f68-b9e7-89357b0e2ade)
![Screenshot (76)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/55a47cfd-eb00-4349-836c-876afcb81858)
![Screenshot (86)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/d05f8939-cda4-49a1-90be-5b3d722d3935)
![Screenshot (85)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/70df9ca1-e687-4142-b05f-c6e051872791)
![Screenshot (84)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8dbe4841-b63c-4ce9-a0e7-fb30d870c222)
![Screenshot (83)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/cfc22414-67b8-42f4-bc32-230b27fd9941)
![Screenshot (82)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/3e05c4bf-38dd-4f90-9db2-7ea6b6346d5c)
![Screenshot (81)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/6caf6e97-5d92-4c94-9f54-938775f03974)
![Screenshot (80)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8b60b3ae-0203-4900-afef-7a83f8f64d0b)
![Screenshot (79)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/bf5dea2f-fb99-429d-b6f6-818efb18b629)
![Screenshot (78)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/4a770c34-3fb3-42b7-927f-77ffca9ad350)
![Screenshot (77)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/c36747ef-b1b8-4a45-914c-e489386c69db)
![Screenshot (88)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8ad6774d-2672-4b69-8ce3-0846d4bb99b4)
![Screenshot (87)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/cb36c6e7-8092-4bb2-8ba2-091f81a54e5b)


![Screenshot (101)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/0dce44fd-5ecd-4f8f-b18a-ebce73ef005b)
![Screenshot (100)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/0c4e16e1-c099-4aa3-a829-80fe57a096c1)
![Screenshot (99)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/07436e46-bae5-41ab-9536-d266ccfa9ac9)
![Screenshot (98)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/c87270dd-48ad-4004-a9f9-44754dc98b4b)
![Screenshot (97)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/3792dd09-6a0e-479a-bfc8-8ff09ebb6fe5)
![Screenshot (96)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/9c178a34-beaa-4160-9fca-1397b6f9b25a)
![Screenshot (95)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/f9c01124-87af-4609-a37d-6e3058e7e45c)
![Screenshot (90)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/e8f41705-bc94-49d2-b55a-a46d97a134cf)
![Screenshot (89)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/c352e82a-cc30-4654-b4fe-5b300dda4bbe)
![Screenshot (104)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/25e82071-0a31-42d2-81b7-3d73effd537f)
![Screenshot (103)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/18c5857a-3c53-4881-9222-3b1fbb115fe7)
![Screenshot (102)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/6c3c7f62-40a7-4202-967e-ed403798376e)

![Screenshot (111)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/91e9cac9-3f91-4a56-8d55-3ff024b30a42)
![Screenshot (110)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/747089fe-c933-425c-8ee8-0bde26cb1d96)
![Screenshot (109)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/6da30f03-c405-4c8a-9d50-7426cc2d4bcf)
![Screenshot (108)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ad7a4945-5ed6-4474-858c-be664af69762)
![Screenshot (107)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/97ba3d4d-caad-4562-bd73-401c1ea0cf19)
![Screenshot (106)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/2dd7605f-e1ad-4160-8791-c00804aa7adc)
![Screenshot (105)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8de31864-e1bb-4186-99e3-2f394ca32c70)
![Screenshot (113)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8f768a60-68dd-4221-93b5-18ece1f729b4)
![Screenshot (112)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/29c0d1f4-d5d6-4a6f-80dc-e771234345d4)


________________________________________________________________________________________________________________________________________________________________________________________________________






