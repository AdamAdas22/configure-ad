
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

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Step 1:Installing Active Directory Domain Services</h2>

<p>
In this step, we will install Active Directory Domain Services (AD DS) on DC-1. This is essential for setting up a domain controller and managing network resources efficiently.
</p>

<h3>Step-by-Step Installation</h3>

<p>
Follow these steps to install AD DS:
</p>

<ul>
  <li>Log in to <strong>DC-1</strong> and open the <strong>Server Manager</strong>.</li>
  <li>Click <strong>Add Roles and Features</strong> to begin the installation process.</li>
  <li>In the <strong>Server Roles</strong> section, check the box for <strong>Active Directory Domain Services</strong> and click <strong>Next</strong>.</li>
  <li>Proceed through the installation wizard until you reach the confirmation page.</li>
  <li>Enable the option to <strong>Restart the server if required</strong> and click <strong>Install</strong>.</li>
  <li>Wait for the installation to complete and then click <strong>Close</strong>.</li>
</ul>

<h3>Next Steps: Promoting DC-1 as a Domain Controller</h3>

<p>
Now that AD DS is installed, the next step is to promote <strong>DC-1</strong> as a domain controller. We will configure Active Directory to manage authentication and domain resources.
</p>

<p><strong>Continue to the next step to complete this process.</strong></p>








<h2>Step 2: Promoting DC-1 to a Domain Controller</h2>

<p>
Now that Active Directory Domain Services is installed, we need to promote <strong>DC-1</strong> to a domain controller. This step will configure the server to manage authentication and network resources within a domain.
</p>

<h3>Step-by-Step Promotion</h3>

<ul>
  <li>Click the <strong>flag icon</strong> at the top-right corner of the screen.</li>
  <li>Select <strong>Promote this server to a domain controller</strong>.</li>
  <li>Choose <strong>Add a new forest</strong> and set the root domain name as <strong>mydomain.com</strong>, then click <strong>Next</strong>.</li>
  <li>For the Directory Services Restore Mode (DSRM) password, enter <strong>password1</strong> and confirm it.</li>
  <li>Leave the <strong>Create DNS delegation</strong> box <strong>unchecked</strong> and click <strong>Next</strong>.</li>
  <li>At the <strong>Prerequisites Check</strong>, click <strong>Install</strong> and wait for the process to complete.</li>
  <li>The system will automatically sign you out once the installation is finished.</li>
</ul>

<h3>Logging Back into the Domain Controller</h3>

<p>
Now that DC-1 has been promoted, you must specify the domain when logging back in. Follow these steps:
</p>

<ul>
  <li>Log back into the virtual machine.</li>
  <li>Because this is now a domain controller, you must log in using the domain.</li>
  <li>For this lab, enter the username as <strong>mydomain.com\labuser</strong> and proceed with login.</li>
</ul>

<p><strong>Congratulations! DC-1 is now a domain controller.</strong> Continue to the next step to configure additional settings.</p>






<h2>Step 3: Creating an Organizational Unit (OU) in Active Directory</h2>

<p>
In this step, we will create an <strong>Organizational Unit (OU)</strong> called <strong>_EMPLOYEES</strong> within Active Directory Users and Computers (ADUC). 
Organizational Units act as folders that help organize users, computers, and groups within a domain. They allow administrators to manage policies, permissions, and security settings efficiently.
</p>

<h3>Why Organizational Units Matter</h3>

<p>
Having a <strong>Domain Administrator</strong> role is a big responsibility, as changes can impact thousands of accounts. Organizing users into OUs ensures structured management, making it easier to apply policies and permissions.
</p>

<h3>Creating the _EMPLOYEES Organizational Unit</h3>

<ul>
  <li>Click the <strong>Windows Start Bar</strong> and open <strong>Active Directory Users and Computers (ADUC)</strong>.</li>
  <li>In the left-hand panel, find and expand your domain (e.g., <strong>mydomain.com</strong>).</li>
  <li>Right-click the domain name and select <strong>New → Organizational Unit</strong>.</li>
  <li>Enter the name as <strong>_EMPLOYEES</strong> and check the box that says <strong>Protect container from accidental deletion</strong>.</li>
  <li>Click <strong>OK</strong> to create the Organizational Unit.</li>
</ul>

<p><strong>Great job!</strong> You now have an <em>Organizational Unit</em> to store employee accounts. In the next step, we will add users to this OU.</p>




































        
<br />
