# Azure_Project
Azure Project  Summary: when new file is add to 'BLOB' it will transfer that file to 'FILE SHARE' and get an EMAIL with the CONTENT of the File and also get SMS on PHONE that 'new file is added' and using Storage Sync Service the on premise Client can view the same file which is added to blob.

You can use the resoure group Templete and open azure service called Custom templete and upload this project there
Resource Group Of My Project: https://drive.google.com/file/d/1OEk62gZQLex6W1k6MdAKY9_5DNwjKz45/view


YOUTUBE VIDEO LINK OF PROJECT: https://www.youtube.com/watch?v=Mbb_aJYeyjI

Overview
So, there's a client who wants to access the internet and enter the Azure portal. When they add a blob file, a trigger will be activated in a Logic App. The Logic App will then transfer the file to Azure File Storage so that the on-premises server can also access the files added in the blob. To establish this real-time file synchronization, Azure Storage Sync Services are used to connect the on-premises server and Azure File share unidirectionally.
After the blob content is transferred to the file share, the Logic App calls an API, which sends an email notifying the content that was added or modified. Additionally, a third-party service called Twilio is used to send an SMS to the client's phone indicating that a new blob file has been added.
To create the on-premises environment, Azure Infrastructure as a Service (IaaS) is employed, utilizing a virtual machine (VM) within a subnet of a virtual network. Another subnet in the same virtual network holds a firewall. Incoming public requests first pass through the firewall, which only allows entry to the virtual network if firewall rules are satisfied. The virtual machine is connected to the firewall.
Inside the virtual machine, Azure Storage Sync Services files are installed to establish a connection with Azure File Share. A new disk driver is attached to the PC folder for this purpose. Additionally, Azure Monitor alerts are set up to trigger a warning alert when CPU usage exceeds 50%.

PDF File With ScreenShoots and explanation about project and how can we create this project.
[Azure Project for Logic App By shivam.pdf](https://github.com/ShivamPratap2409/Azure_Project/files/13162108/Azure.Project.for.Logic.App.By.shivam.pdf)

Doc File of same PDF
[Azure Project.docx](https://github.com/ShivamPratap2409/Azure_Project/files/13162111/Azure.Project.docx)
