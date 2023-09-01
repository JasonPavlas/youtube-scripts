Hey guys, Jason here with Jacksonville IT Pros.

I wanted to take a second and cover some basics about Azure Migrate. Then discuss some possible next steps for those thinking about starting your own cloud adoption journey. 
So without further a due, lets get into it. 

# THE WHAT
Starting with the What
 ## The tool 
  Azure Migrate: Discovery and Assessment is the tool. It's a free product used to rehost your VMs and data onto Azure's infrastructure. This type of migration is often referred to as a lift and shift, is one of the most efficient ways to move your stuff into the cloud. A single appliance deployed into your environment collects metadata from the servers, disks, and NIC - plus listens to the installed applications, roles, and features. There is no agent that needs to be installed on all your servers - this one tool essentially allows you to copy/pastes your servers into Azure servers with zero downtime to your existing environment. 

# WHY
 So why use Azure Migrate - well, Because you may want to move your existing workloads into the cloud. There are many reasons businesses chose IaaS over managing their own infrastructure, but this video is about the tool you can use to make it happen. 

  
# HOW
 This can sound crazy, but if you can deploy a VM, you can have this appliance up and running today. Let me show you how. 

 You'll obviously need an Azure subscription. 
 From there, you'll create a resource group, 
 Then go the market place to find Azure Migrate.
 You'll start an Azure Migrate project - and Boom, you're half way there. 

 Now we're in the Migrate Resource and here under Assessment tools, we'll click discover.
 You have the option to use a CSV file, Say from an RVTools report, but that's now how we are going to do it here. We are going to let the Appliance do its thing.

 You'll select likely be in VMware, but they support Hyper-V, physical servers, and the other cloud platforms also.. neat

 Here, we'll name our appliance and generate a key.
 Then download that sucker. 

You'll have to get the OVA from your local machine, into vCenter, then deploy it. [Here](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.vm_admin.doc/GUID-17BEDA21-43F6-41F4-8FB2-E01D275FE9B4.html) is a link to the VMWare docs, but this is also pretty straight forward. 

Once you see that puppy online in your vCetner environment, we can browse to it from your local machine via its FQDN or IP Address. You'll have to be on the same network, but that probably obvious... Anyways, I think I've tried to hit them outside the network before and felt dumb, so maybe I can save you one...

To finish the setup, we need to enter the project key, which you can find here in the Discovery and Assessment section, under the overview tab. Paste it in here and click verify. The appliance will run a couple updates, then we can register it. 

You'll click Logon here, the login with your Azure creds. You'll be redirected to a web browser and login there. Then you'll get a popup with a device code you'll need to paste into the appliance. 
Once you're done here, this section will have a green checkmark and you can collapse it. 

You'll run this check to verify the VMWare SDK is installed. handy dandy link right here if you run into errors, but I suspect you'll be fine. 

Before you can point to the vCetner server, you'll want to add the required credentials. 
You'll need to give VMWare creds, Windows Creds, and if you want to discover SQL, some SQL Sysadmin Creds. then click validate.  These are required so the appliance can authenticate and discover everything you have going on.

Now we can point the appliance to the vCenter server and click start discovery. 

 Don't be afraid to check the docs [Here](https://learn.microsoft.com/en-us/azure/migrate/how-to-set-up-appliance-vmware) for more details about setting up the appliance.

 
 You'll see servers showing up in your Migrate Project within the Azure Portal with about 15 minutes, but the software inventory only runs every 12 hours and the SQL discovery takes a full 24. 
 
 So before you got home for the day and celebrate a job well begun, You'll want to enable the Database Assessment tool. This is part of the Migrate project and also 100% free, it just needs to be enabled and given SA credentials. This tool will look into the tables and give you super specific details and recommendations on any issues that could prevent a smooth migration. 

 After discovery comes the assessments. You can run multiple assessments so you can make an apples to apples comparison of your future cloud environment. [Here](https://learn.microsoft.com/en-us/azure/migrate/best-practices-assessment) are the best practices for your reference.  Your assessments will have confidence scores that will likely start low. These are based on datapoints collected for each VM so letting assessments run during production hours is a good idea.

 When you have an assessment you like, you can start the replication. The appliance orchestrates replication using VMware snapshots and VMware change block tracking. Data goes from the VMs to the appliance on port 9443, then leaves your environment over port 443 to Azure's migration service endpoint. Data integrity is insured in two stages. First, the target and source disks are bitmapped, then these bitmapps compared. Next, Azure computes a checksum for each block of data in the source and destination and compares the checksum. Anything other than identical for these two checks is a fail, and the replication process will fix the mismatch in the next cycle. 

 You know the replication is complete when the you see Test Migration Pending. The test migration does exactly what it sounds like and will alert you to any issues detected. Once this is complete, you'll see the Test Migration Clean Up Pending status. Azure will clean up the extra resources, the show you the Ready to Migrate status letting you know it's ready for game time. 

 One more click and you're ready to rock in Azure! How freaking cool! 

# So What Next
 The [cloud adoption framework](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview) is something you must review. To borrow a line from Simon Sink, start with why - this will expose you to some questions you certainly didn't think about. The [SMART](https://learn.microsoft.com/en-us/assessments/Strategic-Migration-Assessment/) assessment, although it sounds corny, actually offers a lot of value. It's a 15 minute, multiple choice assessment that covers the high level stuff. This should be homework for your executives, IT team, and stakeholders so everyone's on the same page and speaking the same language.
 
 When it's time to rock and roll, you can do it yourself or work with one of the many Microsoft Partners whom are veted and experience making this happen, like [Jacksonville IT Pros](https://jacksonvilleitpros.com/) for example. 

 If this is going to be an internal project, [Microsoft Learn](https://learn.microsoft.com/en-us/training/paths/m365-azure-migrate-virtual-machine/?source=recommendations) will hold your hand though the technical process and the [cloud adoption framework](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview) will serve as your map, compass, and checklist. 

 If you have any questions, drop a comment, swing by JacksonvilleITPros.com and schedule a consultation, or hit the [Find a partner](https://azure.microsoft.com/en-us/partners) link to meet with us or any of the other highly qualified experts that can help. 

 Until then - we'll see ya next time. 

