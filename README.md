
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

<h2>Deployment and Configuration Steps</h2>
<h1>Installing Active Directory Domain Services</h1>
        <p>Follow these steps to install Active Directory on DC-1:</p>
        <ol>
            <li>Log in to <strong>DC-1</strong>.</li>
            <li>Open the <strong>Start</strong> menu and launch <strong>Server Manager</strong>.</li>
            <li>Click <strong>Add Roles and Features</strong>.</li>
            <li>In the <strong>Server Roles</strong> section, check the box for <strong>Active Directory Domain Services</strong>.</li>
            <li>Click <strong>Next</strong> until you reach the confirmation page.</li>
            <li>Check the option to allow the server to <strong>restart</strong> automatically after installation.</li>
            <li>Click <strong>Install</strong> and wait for the process to complete.</li>
            <li>Once installed, click <strong>Close</strong>.</li>
        </ol>
        <p>Next, we will promote DC-1 to a Domain Controller and configure Active Directory.</p>


















        
<br />
