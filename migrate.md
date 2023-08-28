Hey guys, Jason here with Jacksonville IT Pros.

I wanted to take a second and cover some basics about Azure Migrate. Then discuss some possible next steps for those thinking about starting your own cloud adoption journey. 
So without further a due, lets get into it. 


# THE WHAT
Starting with the What
 ## The tool 
  Azure Migrate: Discovery and Assessment is the tool. It's a free product used to rehost your VMs and data onto Azure's infrastructure. This type of migration is often referred to as a lift and shift, is one of the most efficient ways to move your stuff into the cloud. A single appliance deployed into your environment collects metadata from the servers, disks, and NIC - plus listens to the intalled applications, roles, and features. There is no agent that needs to be installed on all your servers - this one tool essentially allows you to copy/pastes your servers into Azure servers with zero downtime to your existing environment. 

# WHY
 So why use Azure Migrate - well, Becuase you may want to move your exisitng workloads into the cloud. There are many reasons businesses choese IaaS over managing thier own infastruciter, but this video is about the tool you can use to make it happen. 

  
# HOW
 This can sound crazy, but it really is just a few clicks, asuming you have the right credentials. 
 First, you'll need to start and Azure subscription. From there, you'll creat a resource group, then start an Azure Migrate project. 
 You'll find Azure Migrate in the market place and it's just a few clicks to name the project and you download the pre configured appliance that does the magic.

 [Here](https://learn.microsoft.com/en-us/azure/migrate/how-to-set-up-appliance-vmware) are the instructions from Microsoft that outline the setup of the appliance, but if you konw how to create a VM, you can get this tool up and running. 
 To start, you'll browse to the appliance and fillin the vCenter Servers IP address and give it credentials for VM and Windows. 

 You'll mainly interact with this product via the Azure Portal, Once you have green checkmarks in here. 
 
 You'll see servers showing up in your Migrate Project within the Azure Portal with about 15 minutes, but the software inventory only runs every 12 hours and the SQL discovery takes takes a full 24. 
 
 So before you got home for the day and celebrate a job well begun, You'll want to enable the Database Assessment tool. This is part of the Migrate project and also 100% free, it just needs to be enabled and given SA credentials. This tool will look into the tabels and give you super specific details and recomendations on any issues that could prevent a smooth migration. 

 After discovery comes the assessments. You can run mulitple assessemtns so you can make an apples to apples comparision of your future cloud environment. [Here](https://learn.microsoft.com/en-us/azure/migrate/best-practices-assessment) are the best practices and some information about how to consider going from SQL Server to Azure SQL Managed Instatnce, for example. 
 Your assessments will have confidence scores that will likley start low. These are based on datapoints collected for each VM so letting assessments run during production hours is a good idea.

 When you have an assessment you like, you can start the replication. The appliance orchestraest replication using VMware snapshots and VMware change block tracking. Data goes from the VMs to the appliance on port 9443, then leaves your environment over port 443 to Azure's migration service endpoint. Data integrity is insured in two stages. First, the target and source disks are bitmapped, then these bitmapps compared. Next, Azure computes a checksum for each block of data in the source and destiniation and compares the checksum. Anything other than identical for these two checks is a fail, and the replication process will fix the mismatch in the next cycle. 

 You know the replication is compolete when the you see Test Migration Pending. The test migration does exactly what it sounds like and will alert you to any issues detected. Once this is complete, you'll see the Test Migration Clean Up Pending status. Azure will clean up the extra resources, the show you the Ready to Migrate status letting you know it's ready for game time. 

 One more click and you're ready to rock in Azure! How freaking cool! 

# So What Next
 The [cloud adoption framework](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview) is something you must review. To borrow a line from Simon Sink, start with why - this will expose you to some questions you certaily didn't think about. The [SMART](https://learn.microsoft.com/en-us/assessments/Strategic-Migration-Assessment/) assessment, although it sounds corny, actually offers a lot of value. It's a 15 minute, multiple choice assessment that covers the high level stuff. This should be homework for your executives, IT team, and stakeholders so everyone's on the same page and speaking the same language.
 
 When it's time to rock and roll, you can do it yourself or work with one of the many Microsoft Partners whome are veted and experiance making this happen, like [Jacksonville IT Pros](https://jacksonvilleitpros.com/) for example. 

 If this is going to be an internal project, [Microsoft Learn](https://learn.microsoft.com/en-us/training/paths/m365-azure-migrate-virtual-machine/?source=recommendations) will hold your hand though the technical process and the [cloud adoption framework](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview) will serve as your map, compase, and checklist. 

 If you have any questions, drop a comment, swing by JacksonvilleITPros.com and schedule a consultation, or hit the [Find a partner](https://azure.microsoft.com/en-us/partners) link to meet with us or any of the other highly qualified experts that can help. 

 Until then - we'll see ya next time. 