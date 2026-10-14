For this lab, I will be creating an Active Directory on my Proxmox-based homelab 

<h2> Firstly, we'll need to install a version of Winodows server in order to act as the Domain Controller for our Active Directory </h2>
click here for that small project

<h2> Now that we're in Windows Server 2022 we need to actually need to promote this server to he Domain Controller </h2>

  -Firstly, we're in the server manager.
  
  <img width="888" height="627" alt="image" src="https://github.com/user-attachments/assets/6fda2e3d-d122-411b-919e-6e8fa9fe8f60" />
 
  -And then we'll rename it to make things easier from here- Its a lab, and an active directory, so LAB-AD
  
  <img width="885" height="627" alt="image" src="https://github.com/user-attachments/assets/c013d819-f471-4d1d-ace0-4730c93e8a28" />
  
  -Then it restarts, but afterwards, we'll see our name has been changed in the properties 
  
  <img width="269" height="125" alt="image" src="https://github.com/user-attachments/assets/2cba6d14-9c17-418d-a069-e01b89ecd026" />

<h2> Now, we'll create a static IP for the domain controller </h2>
It'd be bad if the domain controller's IP changed every once a while, the user's machines would have to change their connection every time, however...

  **We have a problem**
  -We're currently in a virtual machine, and we do not have internet in the first place to have an IP, let alone a static IP.

  **How we're going to fix this**
  -We'll get internet.

<h2> Getting internet on the virtual machine </h2>

  -First, we'll head into Device Manager
  
  <img width="677" height="490" alt="image" src="https://github.com/user-attachments/assets/3ed16ed5-faff-4765-a873-5d3375abf75b" />

  -We have to update the ethernet controller- there is no driver currently. Luckily for us, the ethernet controller is located in the earlier installed VirtIO drivers we installed when installing Windows Server
  
  <img width="677" height="490" alt="image" src="https://github.com/user-attachments/assets/920fe00b-c6d7-4964-b48d-c27b4aea1002" />

  -We'll click update drivers, then browse our computer for drivers. We'll find the NetKVM in the virtIO CD drive, and go to the 2k22 folder
  
  <img width="590" height="387" alt="image" src="https://github.com/user-attachments/assets/b4c9602b-f39f-4e02-a102-9503e6207239" />
  
  <img width="246" height="177" alt="image" src="https://github.com/user-attachments/assets/76a645fc-8c4b-4a6f-8042-7e2d61266daa" />
  
  -Now, we have internet
  
  <img width="806" height="383" alt="image" src="https://github.com/user-attachments/assets/0d8fab6d-fa5b-4040-9aa8-55760045296f" />

  <h2> Making a static IP for the domain controller (Actually this time) </h2>

  -First, we'll head into Network Connections, properties, find network protocol v4, then configurations

  <img width="685" height="511" alt="image" src="https://github.com/user-attachments/assets/e77da432-20e5-4384-bb92-7eb4ce93e3fd" />

  <img width="308" height="404" alt="image" src="https://github.com/user-attachments/assets/ace2bd0a-68d9-4be0-92e6-94100a1fbbd1" />

  <img width="343" height="393" alt="image" src="https://github.com/user-attachments/assets/042fdf25-a4eb-4f9f-b083-f4f7bc1220c3" />

  -We'll make the static IP 192.168.1 for privacy, and .10 for the domain controller. .1 will be reserved for the default gateway to reserve for the router. Subnet mask will be 255.255.255.0, and the dns will refer to Google by using 8.8.8.8, with 8.8.4.4 as a backup also for Google

  <img width="348" height="391" alt="image" src="https://github.com/user-attachments/assets/18b5af6e-4f69-4d31-b15b-20033af2ac12" />

  



  

  


  
