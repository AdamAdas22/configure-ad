
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

<h2>Installing Active Directory Domain Services</h2>

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



















        
<br />
