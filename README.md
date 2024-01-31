
<p align="center">

  ![azure](https://github.com/mehmhacimic/configure-ad/assets/157438082/5b36965b-bdc4-446c-97f7-a3c47f1683d0)
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/> 


<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure 
- Remote Desktop Connection
- Active Directory Domain Services
- PowerShell/Command Prompt

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 

<h2>High-Level Deployment and Configuration Steps</h2>

1. Create a Microsoft Azure account. 
2. Start a free trial or choose the pay as you go option. 

<h2>Deployment and Configuration Steps</h2>

1. Create a Domain Controller virtual machine(VM1) using Windows Server 2022. Name it whatever you you want to, I named mine Roman-Reigns. Create a username and password as well and do not forget it. I am using "tripleh" as my username for this demonstration (also take note of the resource group and virtual network that is created)
   
![AD1](https://github.com/mehmhacimic/configure-ad/assets/157438082/d4f06a65-a473-456b-b143-de8ece17f619)

2. After the Domain Controller virtual machine(VM1) finishes deploying, create a Client virtual machine(VM2) using Windows 10 and again, name it whatever you want. Make sure you assign it to the same resource group and virtual network as the Domain Controller VM.
3. While waiting for the Client VM(VM2) to deploy, change the Domain Controller's NIC private IP address from dynamic to static.
   
![AD2](https://github.com/mehmhacimic/configure-ad/assets/157438082/60f94e75-281b-412c-85ce-098152bd499a)
![AD3](https://github.com/mehmhacimic/configure-ad/assets/157438082/2d808936-4402-4b2c-a82a-fec33e88103e)

4. Log into VM1 and enable ICMPv4 on the local windows firewall.
   
![AD5](https://github.com/mehmhacimic/configure-ad/assets/157438082/332f3529-654f-4ecb-bd2a-b27d416f4617)


5. Log into VM2 and ping VM1's private IP address to ensure connectivity between the Client and the Domain Controller.
6. Now, log into VM1 and open up Server Manager(if not already opened). Click on 'Add roles and features' and continue until prompted to select server roles. Check off 'Active Directory Domain Services' and hit install.

![AD7](https://github.com/mehmhacimic/configure-ad/assets/157438082/bc4260a6-1509-4b03-9d33-c27aba3ca002)

7. Promote the server as a domain controller and set up a new forest. You can use whatever you want as the domain name, just take note of it and do not forget it. I am using "wwe.com" for this demonstration.

![AD8](https://github.com/mehmhacimic/configure-ad/assets/157438082/639b57fd-0251-4d12-b526-1603b1cfc227)

8. Restart VM1 and log back in as wwe.com\tripleh
9. Now, you can go into Active Directory Users and Computers(ADUC) and customize your directory to fit your needs.
10. For each client computer, you will need to add it to your domain. Go into the Azure Portal and set VM2's(mine is named Rhea-Ripley) DNS settings to VM1's private IP address.
 > Network interface
    > DNS servers
      > Custom
        > Insert VM1's private IP address into the "Add DNS servers" field and hit save. 

![AD10](https://github.com/mehmhacimic/configure-ad/assets/157438082/10432251-b00e-4dc4-8a0f-e833544bc860)







