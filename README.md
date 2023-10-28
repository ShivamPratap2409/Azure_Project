# Azure_Project
**Project Summary:** 
when new file is add to 'BLOB' it will transfer that file to 'FILE SHARE' and get an EMAIL with the CONTENT of the File and also get SMS on PHONE that 'new file is added' and using Storage Sync Service the on premise Client can view the same file which is added to blob.

You can use the resoure group Templete and open azure service called Custom templete and upload this project there
Resource Group Of My Project: https://drive.google.com/file/d/1OEk62gZQLex6W1k6MdAKY9_5DNwjKz45/view

**8 mins shot video about project*:* https://www.youtube.com/watch?v=-HVB4Hsj4kQ
__*FULL YOUTUBE VIDEO LINK OF PROJECT:*__ https://www.youtube.com/watch?v=Mbb_aJYeyjI

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


__For Screenshots and proper project information how it is create please refer the PDF file attached__

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


![Screenshot (162)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/7e57c918-767c-4c39-8bd7-fe4be43bbf6a)
![Screenshot (161)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/487f8374-01a6-4107-ab36-d78f233d96c0)
![Screenshot (160)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/b84867ce-f6ad-4d9e-8f83-98aa3255f64f)
![Screenshot (159)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/89d3ceec-93e5-4dc0-bc3a-875770df3ada)
![Screenshot (158)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/aedd951d-4785-4c2e-b8d5-82aac1d223a2)
![Screenshot (157)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/99770dfe-cb22-4f57-816f-6cf112545b86)
![Screenshot (156)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/0d4d4ada-f800-4aa2-87ef-318bbc5d7dd0)![Screenshot (183)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/638b1866-9a32-4260-b680-a3937431c045)
![Screenshot (182)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/821a274a-e191-441e-9e53-9d382fc3af5c)
![Screenshot (181)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/71000c37-0e06-46ff-84d7-75067fe5be70)
![Screenshot (180)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/5edeb826-6230-49b4-89b2-0b9e856bca33)
![Screenshot (179)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8b136c9c-4ce7-4742-adfd-7c5c10d99ec3)

![Screenshot (155)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/0afa253c-bd4b-46a5-a29f-812a6c67c645)
![Screenshot (154)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/581575ec-3657-4ff7-a0ea-46ec13a51cec)
![Screenshot (153)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/312160fb-568d-48b5-9d4d-34f77917b568)
![Screenshot (152)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/0c8b0d79-68eb-4815-a8a2-4794b55efe0e)
![Screenshot (151)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/6a6d7cf5-a8ed-4105-b874-7f1653b366dd)
![Screenshot (150)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/2bb80dba-b307-4f90-ae30-30edda4c27c9)
![Screenshot (149)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/b852453e-352b-4635-8bcb-1f25770ca1e4)
![Screenshot (148)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/7958da8f-f4e4-445e-ad56-2d027361e64e)
![Screenshot (147)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/48157f07-63b6-49ff-bf7d-6d604cac39a9)
![Screenshot (146)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/d3074bd1-5769-4ba0-8e0e-1a60714e081c)![Screenshot (176)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/6fbf2c66-1634-4127-86c6-c8100f810a53)

![Screenshot (145)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/1fac91d4-06e7-421b-a5b3-78c53a07805e)
![Screenshot (144)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/48ca54f0-a9a7-48c7-b1da-45fe39ba64c9)![Screenshot (178)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8e5617ab-6ef4-48ca-a8f5-7b34b157880d)

![Screenshot (143)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ddd0e36f-ba26-4cd9-a986-8790937b8f3e)
![Screenshot (142)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/f67a0764-1586-4a9f-802c-f424df4e39f2)
![Screenshot (141)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/df72a4f6-3977-417e-b3fa-b1cd867ca07a)![Screenshot (177)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/fe19bd24-8095-491c-9599-90b55f20eaca)

![Screenshot (140)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/45095f7e-bb5c-4d96-a7a6-63d9a10662b2)
![Screenshot (163)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ce182fc0-0fd5-45ef-a0bd-d968fed6f746)

![Screenshot (175)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/c3540358-c71e-46da-a2f0-651b2d0fb867)
![Screenshot (174)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/55b074b1-d174-4743-95e8-4515c34af048)
![Screenshot (173)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8a320eb6-97ac-4845-af1e-e3e978966718)
![Screenshot (172)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/2995f8f9-a380-44b3-a248-c82dc1560677)
![Screenshot (171)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/b1fb6d87-91b9-4594-8041-3cb991052ac7)
![Screenshot (170)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/90da2bf9-b65e-41f7-9411-33e34c8243f5)
![Screenshot (169)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/5b53cfa3-4671-4a67-b907-a056f01823c1)
![Screenshot (168)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/1f367265-d8fb-4360-8462-075cafc153b5)
![Screenshot (167)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/12047c13-8f5f-48f8-9e97-f066cc769b33)
![Screenshot (166)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/1e6447a7-7f9e-45a6-b68c-911a2f33e13f)
![Screenshot (165)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/02b4c91d-ac4e-46f9-972e-af6430d86196)
![Screenshot (164)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/eb42220c-a833-4946-ae4e-e05577aa81a2)
![Screenshot (187)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/a9bec5ff-a08f-4bb6-9b0e-22b4893b57c3)
![Screenshot (186)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8ab1fde1-7e03-4ed1-9c50-6d62eef78cb2)
![Screenshot (185)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/6d01df50-a242-425e-a44d-8f70b987c920)
![Screenshot (184)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/3ef3c71e-727d-4991-b331-81df30424aca)



![Screenshot (203)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/c29249a8-542d-4a69-aac9-9617d65948be)
![Screenshot (202)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/4a21f3f2-bfb2-433b-a970-b40bf058296b)
![Screenshot (201)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ca03d121-43ac-4e2b-a07c-522815f75de9)
![Screenshot (200)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/5e723091-874c-4874-8d16-d0cf51affa00)
![Screenshot (199)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/e721a1ac-2dd3-4a46-8837-13fe27d9086e)
![Screenshot (198)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/c3d08893-7084-434a-9990-7a44b57a5e84)
![Screenshot (197)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/68bbe98b-60c3-4c50-a656-d01e670e6866)
![Screenshot (196)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/75e1bc8d-8e0c-4839-80da-100f9e0ad586)
![Screenshot (195)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/44dfb0e3-5084-4177-b5fb-1342e4d4dccd)
![Screenshot (194)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/e54b243b-e08c-475b-abb7-5afa6061105b)
![Screenshot (193)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/fc26e5e1-01c8-4999-96aa-578bb7cc3684)
![Screenshot (192)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/08317f8e-ebff-4d31-b6e9-ab4b8dc30224)
![Screenshot (191)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/a0b74ef1-765e-4fd1-973d-20ed1a3e14e7)
![Screenshot (190)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/085a652f-e1ee-4f07-a8e9-5e872a41ac84)
![Screenshot (189)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/9548e2bc-1cf1-47ff-a99c-d62a6511af91)
![Screenshot (188)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/058e8b56-a971-4f18-a5b8-5f402fb7c100)
![Screenshot (211)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/2931de1d-5572-4f8f-a488-1ac1fe78446c)
![Screenshot (210)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/a2712469-f586-47d3-a28b-e2d17cd497e4)
![Screenshot (209)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/6f9cb605-af3e-4852-888b-fa92b18c1089)
![Screenshot (208)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/8070c5ec-bad7-4dfd-b9d5-b287e494f91e)
![Screenshot (207)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/9471e35f-8b57-4c40-8a2b-5de39ef87dfc)
![Screenshot (206)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/aabcce25-5bba-41fc-b732-31372562ad6e)
![Screenshot (205)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/29c3d960-ae30-4138-a1c7-76f3f45e03b6)
![Screenshot (204)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ebbb9ab8-ebb5-423b-9a8d-0cbe3cc84c22)


![Screenshot (259)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/673c4fcb-a10d-4f52-bb63-c1b2c6a67869)
![Screenshot (258)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/3f56b42a-3c98-41b0-9f26-cb4b124d78c7)
![Screenshot (257)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/700680fb-294b-48d2-b5de-004884ae50a1)
![Screenshot (256)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/4a42ab72-915f-41c4-8af5-33a0d4c874ec)
![Screenshot (243)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/a8976528-1cbe-4ceb-b9c7-9ec8775ff0c9)
![Screenshot (242)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/a114b903-d504-4760-9f46-1188eeb06d15)
![Screenshot (241)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ec0c5196-421d-4bc3-84e7-fb126bfc631b)
![Screenshot (240)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/bebaee5d-7ff9-4692-8b36-0d8a2c1e3496)
![Screenshot (239)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/e16040dc-b436-42db-8fec-030549eaa74f)
![Screenshot (238)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/97423362-d631-468c-8a90-cda973e4d8a4)
![Screenshot (237)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/2c926c4a-d574-4503-a36a-649b9f31a94b)
![Screenshot (236)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/b374ddc4-5467-445d-8f46-4c0fc0a7c27f)
![Screenshot (235)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/ffc8e283-d556-4cea-92aa-b5b4c1caac73)
![Screenshot (234)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/daa5ca0c-9540-4ca0-82bf-612dede88f1a)
![Screenshot (233)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/a80c138f-d8e2-4b92-9409-2a05210bef56)
![Screenshot (232)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/f90102e1-ac55-4732-94f1-8f8184f41bbe)
![Screenshot (231)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/7f56bca8-41f1-4b64-acff-bbf3caff71c3)
![Screenshot (230)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/0c145c87-9db4-4b5e-af92-14d2bf2b1c26)
![Screenshot (229)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/e815597f-40dc-4593-9ca3-c4db2d812f07)
![Screenshot (228)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/bbae1d24-71b4-4225-aa67-eb5e4c5b4db9)
![Screenshot (227)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/d488672b-a42b-4815-9d97-8fca6c552598)
![Screenshot (226)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/3a052ef6-ce5a-459e-8766-9ed0d6a48882)
![Screenshot (225)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/16b55c70-d696-4d7d-87d9-4cf93a5fd417)
![Screenshot (224)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/65030266-d065-42b9-8eb6-304b65b96651)
![Screenshot (223)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/14b8aab1-a03b-42bf-9516-821ed3da58b2)
![Screenshot (222)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/2baff81c-7615-4392-b8e4-dc694d7b1b03)
![Screenshot (221)](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/cb91f656-a5b1-498e-b42b-c8442fb2dc3a)




________________________________________________________________________________________________________________________________________________________________________________________________________






