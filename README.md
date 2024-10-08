<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

**Note: We will be switching between two virtual machines we've created DC-1 which is a Domain Controler VM (Windows Server 2022), and Client-1, which is a Desktop VM (Windows 10) .**

<br />

![1](https://github.com/user-attachments/assets/eee15e89-77d0-4087-bdf5-257cd1808bbc)

<br />

![2](https://github.com/user-attachments/assets/715a49a5-619d-48a4-ab2c-7cf3031ffa01)

<br />

![3](https://github.com/user-attachments/assets/d8ef10c1-64b2-4e91-a050-76e9f967d27d)

<br />

1) Utilizing DC-1 in Active Directory Users and Computers (ADUC), We create an Organizational Unit (OU) called “_EMPLOYEES” and create a new OU named “_ADMINS.”

To create an Organization Unite right click your domain-> New-> Organizational Unit

<br />
<br />

![4](https://github.com/user-attachments/assets/dc19edb0-a84f-4b5f-8bcb-46497ef55a13)

2) Create a new employee named "Jane Doe" with the username of "jane_admin.

In _ADMINS right-click select new-> user-> enter name/username.

<br />
<br />

![5](https://github.com/user-attachments/assets/9cdf256b-5bc8-4562-8101-a13060f28f8d)

<br />

![6](https://github.com/user-attachments/assets/ff0c0015-5923-4b7c-ad11-3de359e2f5e4)

<br />

![7](https://github.com/user-attachments/assets/acb25cae-c6e2-412a-bba9-b6221f445231)

<br />

 3) Add jane_admin to the "Domain Admins" Security Group.

In _ADMINS right right-click user jane doe-> Select properties-> Click tab "Member Of"-> Click Add-> Select Domain Admin-> Click OK, Apply, then OK.

<br />
<br />

![8](https://github.com/user-attachments/assets/f6d47a43-9167-467b-a38c-a5a9d17f02cd)

<br />

4) Log out/close the Remote Desktop connection to DC-1 and log back in as "mydomain.com\janeadmin."

<br />
<br />

![12](https://github.com/user-attachments/assets/b40b9dfa-57d3-4d9f-91f1-bf673e285cd1)

<br />

![13](https://github.com/user-attachments/assets/7872449a-7000-470b-9744-9cfa3c155372)

<br />

![14](https://github.com/user-attachments/assets/9c04451d-1084-4404-bc19-e6845163a6f3)

<br />

5) From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address and restart Client-1.

In Virtual Machines select Client-1-> Networking->Network Setting- Click client1635_z1-> Select Custom DNS Server->Input DC-1 IP Address.
 
<br />
<br />

![9](https://github.com/user-attachments/assets/32d08f60-8578-4be1-a12f-614b2cdba78d)

<br />

![10](https://github.com/user-attachments/assets/326e323c-a0b9-4e8f-a2d3-7569a01d0659)

<br />

![11](https://github.com/user-attachments/assets/4cfbcb24-c742-479a-a4c0-aa9335c5ebcf)

<br />

6) Utilizing Client-1 to join into the Domain.

We go to the system's settings -> rename this PC advanced-> Change.

<br />
<br />

![15](https://github.com/user-attachments/assets/63b46809-c3cb-43d0-b66b-efe4be527bd3)

<br />

![16](https://github.com/user-attachments/assets/24e8e17d-bf61-4cc7-a190-8ad784084f15)

<br />

![17](https://github.com/user-attachments/assets/6175b821-dd95-4657-8e61-a94a2b03ba32)

7) We enter the domain name and log in with jane_admin. 

<br />
<br />

![18](https://github.com/user-attachments/assets/bae7df66-2475-4a3e-ad59-d826071960cb)

**Note: Client1 will need to restart. You can verify the changes in the system settings about section- "Full Device Name."**

<br />
<br />

![19](https://github.com/user-attachments/assets/e8c52095-5737-4540-ae41-9543f76f07b2)

<br />

![20](https://github.com/user-attachments/assets/3d21718e-9961-4cfb-8a57-42ef847d9363)

<br />

![21](https://github.com/user-attachments/assets/2d113c8c-7603-4896-b85d-e5c530d3d389)

8) From the settings page we select Remote Desktop->Select users that can remotely access this PC-> Add-> Enter domain users.

<br />
<br />

![22](https://github.com/user-attachments/assets/f68e0dbe-741d-4daf-9610-be884400fa8c)

9) Utilizing DC-1 from the start menu search Windows Power Shell and run as Administrator. 

<br />
<br />

![23](https://github.com/user-attachments/assets/17b85c49-e3a3-4b8e-9655-13fd525f9983)

<br />

![24](https://github.com/user-attachments/assets/14d6a20b-d252-480e-8862-54a3af4ec88c)

10) We create a new file in Windows Powershell and copy a script to create random users.
    
<br />
<br />

![25](https://github.com/user-attachments/assets/dea3b056-124a-42de-8ffc-6f8d89e04521)

<br />

![26](https://github.com/user-attachments/assets/196c1d5d-1d46-44ea-aa81-a3da38e7028c)

<br />

![27](https://github.com/user-attachments/assets/3000cd5a-c839-439f-afe4-3e918293b605)

  
<br />

![28](https://github.com/user-attachments/assets/e7349391-4b13-4194-a221-13ded11f0bd3)

11) We select a user from Active Directory and test login with Client 1, then open the command line and run commands "whoami" and "hostname."

<br />  
<br />

![29](https://github.com/user-attachments/assets/2b92edf7-a3e7-4923-9d0f-f8b732aaba3c)

<br />

![30](https://github.com/user-attachments/assets/1cc1de5e-a505-486f-9104-f8a96e231f5f)

12) From DC-1 utilizing Active Directory, we can reset the password by right-clicking the user and selecting reset password. We have the option of setting a New Password or we can unlock the user's account if the user remembers their password. 

<br />
<br />

![31](https://github.com/user-attachments/assets/0052d48e-07a8-4b90-aec2-d4b9eb18da8a)

13) We can also unlock the user account by right-clicking the User-> Selecting properties-> Selecting Account Tab-> Select "Unlock account"-> Clicking apply then OK. 

<br />
<br />

![29](https://github.com/user-attachments/assets/2b92edf7-a3e7-4923-9d0f-f8b732aaba3c)

<br />

![32](https://github.com/user-attachments/assets/a94ba34f-b4c8-4217-be5b-92ada67a37b8)

14) We can also disable the account by right-clicking the User account and selecting Disable. 

<br />
<br />

![33](https://github.com/user-attachments/assets/94509cd0-4f35-4d61-9b9b-1959eb24160b)

<br />

![34](https://github.com/user-attachments/assets/9d812d16-c696-4a51-a640-41ac11b2a304)

15) Utilizing client-1 We attempt to log in with the disabled account and get an error message stating the User account is disabled. 
