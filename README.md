# Azure_Project
Azure Project  Summary: when new file is add to 'BLOB' it will transfer that file to 'FILE SHARE' and get an EMAIL with the CONTENT of the File and also get SMS on PHONE that 'new file is added' and using Storage Sync Service the on premise Client can view the same file which is added to blob.

You can use the resoure group Templete and open azure service called Custom templete and upload this project there
Resource Group Of My Project: https://drive.google.com/file/d/1OEk62gZQLex6W1k6MdAKY9_5DNwjKz45/view


YOUTUBE VIDEO LINK OF PROJECT: https://www.youtube.com/watch?v=Mbb_aJYeyjI

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Overview
So, there's a client who wants to access the internet and enter the Azure portal. When they add a blob file, a trigger will be activated in a Logic App. The Logic App will then transfer the file to Azure File Storage so that the on-premises server can also access the files added in the blob. To establish this real-time file synchronization, Azure Storage Sync Services are used to connect the on-premises server and Azure File share unidirectionally.
After the blob content is transferred to the file share, the Logic App calls an API, which sends an email notifying the content that was added or modified. Additionally, a third-party service called Twilio is used to send an SMS to the client's phone indicating that a new blob file has been added.
To create the on-premises environment, Azure Infrastructure as a Service (IaaS) is employed, utilizing a virtual machine (VM) within a subnet of a virtual network. Another subnet in the same virtual network holds a firewall. Incoming public requests first pass through the firewall, which only allows entry to the virtual network if firewall rules are satisfied. The virtual machine is connected to the firewall.
Inside the virtual machine, Azure Storage Sync Services files are installed to establish a connection with Azure File Share. A new disk driver is attached to the PC folder for this purpose. Additionally, Azure Monitor alerts are set up to trigger a warning alert when CPU usage exceeds 50%.

PDF File With ScreenShoots and explanation about project and how can we create this project.
[Azure Project for Logic App By shivam.pdf](https://github.com/ShivamPratap2409/Azure_Project/files/13162108/Azure.Project.for.Logic.App.By.shivam.pdf)

Doc File of same PDF
[Azure Project.docx](https://github.com/ShivamPratap2409/Azure_Project/files/13162111/Azure.Project.docx)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




Flow Chat of Project:
![flow-1](https://github.com/ShivamPratap2409/Azure_Project/assets/140940680/7392ff3a-1511-4b1d-946f-010fe8d48065)




Flow chat explanation 

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


