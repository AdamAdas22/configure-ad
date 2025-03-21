
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











<h2>Creating an Administrative Organizational Unit (OU) and Adding a New Employee</h2>

<p>
Now that we have set up the <strong>_EMPLOYEES</strong> OU, we will create another Organizational Unit called <strong>_ADMINS</strong>. This will be used to manage administrative accounts separately from regular employees.
</p>

<h3>Step 1: Create the _ADMINS Organizational Unit</h3>

<ul>
  <li>Open <strong>Active Directory Users and Computers (ADUC)</strong>.</li>
  <li>Expand your domain (e.g., <strong>mydomain.com</strong>).</li>
  <li>Right-click your domain name and select <strong>New → Organizational Unit</strong>.</li>
  <li>Enter the name as <strong>_ADMINS</strong> and check the box <strong>Protect container from accidental deletion</strong>.</li>
  <li>Click <strong>OK</strong> to create the Organizational Unit.</li>
</ul>

<h3>Step 2: Create a New Administrative User</h3>

<ul>
  <li>In ADUC, navigate to the newly created <strong>_ADMINS</strong> OU.</li>
  <li>Right-click on <strong>_ADMINS</strong> and select <strong>New → User</strong>.</li>
  <li>In the <strong>First Name</strong> field, enter: <strong>Jane</strong></li>
  <li>In the <strong>Last Name</strong> field, enter: <strong>Doe</strong></li>
  <li>In the <strong>User logon name</strong> field, enter: <strong>jane_admin</strong></li>
  <li>Click <strong>Next</strong> to proceed.</li>
</ul>

<h3>Step 3: Set a Password for Jane Doe</h3>

<ul>
  <li>Enter the password: <strong>Cyberlab123!</strong></li>
  <li>Uncheck <strong>User must change password at next logon</strong>.</li>
  <li>Check <strong>Password never expires</strong> (for training purposes).</li>
  <li>Click <strong>Next</strong>, then <strong>Finish</strong> to create the user.</li>
</ul>

<p><strong>Success!</strong> You have now created an administrative account for Jane Doe. Next, we will configure permissions and roles for administrative users.</p>











<h2>Step 4: Assigning Jane Doe to the "Domain Admins" Security Group</h2>

<p>
Now that we have created the administrative user <strong>jane_admin</strong>, we need to grant her domain administrator privileges. This will allow her to manage Active Directory settings across the domain.
</p>

<h3>Step 1: Add Jane Doe to the "Domain Admins" Group</h3>

<ul>
  <li>Open <strong>Active Directory Users and Computers (ADUC)</strong>.</li>
  <li>Navigate to the <strong>_ADMINS</strong> Organizational Unit.</li>
  <li>Right-click on <strong>Jane Doe (jane_admin)</strong> and select <strong>Properties</strong>.</li>
  <li>Go to the <strong>Member Of</strong> tab.</li>
  <li>Click <strong>Add</strong>, then type: <strong>Domain Admins</strong>.</li>
  <li>Click <strong>Check Names</strong> to ensure it resolves properly.</li>
  <li>Click <strong>OK</strong>, then <strong>Apply</strong>, and finally <strong>OK</strong> again.</li>
</ul>

<h3>Step 2: Log Out and Reconnect as jane_admin</h3>

<ul>
  <li>Close the Remote Desktop Connection to <strong>DC-1</strong>.</li>
  <li>Reopen Remote Desktop and log in with the following credentials:</li>
  <ul>
    <li><strong>Username:</strong> <code>mydomain.com\jane_admin</code></li>
    <li><strong>Password:</strong> <code>Cyberlab123!</code></li>
  </ul>
  <li>Once logged in, verify that you have administrative privileges by opening <strong>Server Manager</strong> or <strong>Active Directory Users and Computers (ADUC)</strong>.</li>
</ul>

<h3>Step 3: Use jane_admin as Your Admin Account</h3>

<p>
From this point forward, <strong>jane_admin</strong> will be used as the primary administrative account for managing the domain. 
This ensures that all administrative actions are logged under a dedicated admin user rather than a general system account.
</p>

<p><strong>Congratulations!</strong> Jane Doe is now a domain administrator, and you’re ready to proceed with further configurations.</p>














<h2>Step 5: Joining Client-1 to the Domain (mydomain.com)</h2>

<p>
Now that we have our domain controller (DC-1) set up, we need to join Client-1 to the domain. This will allow Client-1 to authenticate users and access domain resources.
</p>

<h3>Step 1: Verify DNS Settings and Restart (Already Done)</h3>

<ul>
  <li>Client-1's DNS settings should be set to the Domain Controller's Private IP address.</li>
  <li>Restart Client-1 from the <strong>Azure Portal</strong>.</li>
</ul>

<h3>Step 2: Join Client-1 to the Domain</h3>

<ul>
  <li>Log in to <strong>Client-1</strong> as the local administrator (<code>labuser</code>).</li>
  <li>Open <strong>System Properties</strong>:
    <ul>
      <li>Right-click on <strong>Start</strong> and select <strong>System</strong>.</li>
      <li>Scroll down and click <strong>Advanced System Settings</strong>.</li>
      <li>Under the <strong>Computer Name</strong> tab, click <strong>Change</strong>.</li>
    </ul>
  </li>
  <li>Select <strong>Domain</strong> and enter: <code>mydomain.com</code>.</li>
  <li>When prompted, enter domain administrator credentials:
    <ul>
      <li><strong>Username:</strong> <code>mydomain.com\jane_admin</code></li>
      <li><strong>Password:</strong> <code>Cyberlab123!</code></li>
    </ul>
  </li>
  <li>Click <strong>OK</strong>, then restart the computer when prompted.</li>
</ul>

<h3>Step 3: Verify Client-1 in Active Directory</h3>

<ul>
  <li>Log in to <strong>DC-1</strong> as <code>jane_admin</code>.</li>
  <li>Open <strong>Active Directory Users and Computers (ADUC)</strong>.</li>
  <li>Expand the <strong>Computers</strong> container and verify that <strong>Client-1</strong> appears.</li>
</ul>

<h3>Step 4: Organize Client-1 in Active Directory</h3>

<ul>
  <li>In <strong>ADUC</strong>, right-click on the domain and select <strong>New → Organizational Unit</strong>.</li>
  <li>Name the new OU: <strong>_CLIENTS</strong> and click <strong>OK</strong>.</li>
  <li>Drag <strong>Client-1</strong> from the <strong>Computers</strong> container into <strong>_CLIENTS</strong>.</li>
</ul>

<h3>Finishing Up</h3>

<p>
Client-1 is now a part of <strong>mydomain.com</strong> and is properly organized in Active Directory. You can now manage policies, users, and resources for this machine from the domain controller.
</p>


















<h2>Setting Up Remote Desktop for Non-Administrative Users on Client-1</h2>

<p>
Before creating and testing user logins, we need to enable Remote Desktop access for non-administrative users on <strong>Client-1</strong>. Follow these steps to allow domain users to access the machine remotely.
</p>

<h3>Step 1: Start the Virtual Machines</h3>

<ul>
  <li>Log into the <strong>Azure Portal</strong>.</li>
  <li>Turn on both <strong>DC-1</strong> and <strong>Client-1</strong> if they are powered off.</li>
</ul>

<h3>Step 2: Log into Client-1 as an Administrator</h3>

<ul>
  <li>Log into <strong>Client-1</strong> using the administrator account:</li>
  <ul>
    <li><strong>Username:</strong> <code>mydomain.com\jane_admin</code></li>
    <li><strong>Password:</strong> <code>Cyberlab123!</code></li>
  </ul>
</ul>

<h3>Step 3: Open System Properties</h3>

<ul>
  <li>Press <code>Win + R</code>, type <code>sysdm.cpl</code>, and press <strong>Enter</strong>.</li>
  <li>Go to the <strong>Remote</strong> tab.</li>
  <li>Under <strong>Remote Desktop</strong>, select <strong>"Allow remote connections to this computer"</strong>.</li>
</ul>

<h3>Step 4: Allow Domain Users Access</h3>

<ul>
  <li>Click <strong>Select Users...</strong>.</li>
  <li>Click <strong>Add...</strong> and type <code>Domain Users</code>.</li>
  <li>Click <strong>Check Names</strong> to ensure it resolves.</li>
  <li>Click <strong>OK</strong> to apply the changes.</li>
</ul>

<h3>Step 5: Verify Remote Access</h3>

<ul>
  <li>Sign out of <strong>jane_admin</strong>.</li>
  <li>Try logging in remotely using a non-administrative domain user.</li>
</ul>

<h3>Notes</h3>

<p>
Normally, in a real-world scenario, you would configure this setting using <strong>Group Policy</strong> to apply the change to multiple systems at once. This method ensures consistency and reduces manual configuration errors.
</p>

<p>
Now that Remote Desktop access is enabled, proceed with creating multiple users and logging in as one of them in the next step.
</p>






























<h2>Creating Additional Users and Logging into Client-1</h2>

<p>
In this step, we will create multiple users in Active Directory using PowerShell and attempt to log into Client-1 with one of the newly created accounts.
</p>

<h3>Step 1: Log into DC-1</h3>

<ul>
  <li>Log in to <strong>DC-1</strong> as <code>mydomain.com\jane_admin</code>.</li>
  <li>Open <strong>PowerShell ISE</strong> as an administrator.</li>
</ul>

<h3>Step 2: Create a New Script File and name it something like "create-users"</h3>

<ul>
  <li>In PowerShell ISE, click <strong>File</strong> → <strong>New</strong> to create a new script file.</li>
  <li>Copy and paste the entire following script into the new file:</li>
</ul>
# ----- Edit these Variables for your own Use Case ----- #
$PASSWORD_FOR_USERS   = "Password1"
$NUMBER_OF_ACCOUNTS_TO_CREATE = 10000
# ------------------------------------------------------ #

Function generate-random-name() {
    $consonants = @('b','c','d','f','g','h','j','k','l','m','n','p','q','r','s','t','v','w','x','z')
    $vowels = @('a','e','i','o','u','y')
    $nameLength = Get-Random -Minimum 3 -Maximum 7
    $count = 0
    $name = ""

    while ($count -lt $nameLength) {
        if ($($count % 2) -eq 0) {
            $name += $consonants[$(Get-Random -Minimum 0 -Maximum $($consonants.Count - 1))]
        }
        else {
            $name += $vowels[$(Get-Random -Minimum 0 -Maximum $($vowels.Count - 1))]
        }
        $count++
    }

    return $name

}

$count = 1
while ($count -lt $NUMBER_OF_ACCOUNTS_TO_CREATE) {
    $fisrtName = generate-random-name
    $lastName = generate-random-name
    $username = $fisrtName + '.' + $lastName
    $password = ConvertTo-SecureString $PASSWORD_FOR_USERS -AsPlainText -Force

    Write-Host "Creating user: $($username)" -BackgroundColor Black -ForegroundColor Cyan
    
    New-AdUser -AccountPassword $password `
               -GivenName $firstName `
               -Surname $lastName `
               -DisplayName $username `
               -Name $username `
               -EmployeeID $username `
               -PasswordNeverExpires $true `
               -Path "ou=_EMPLOYEES,$(([ADSI]`"").distinguishedName)" `
               -Enabled $true
    $count++

}

<h3>Step 3: Save and Run the Script</h3>


![image](https://github.com/user-attachments/assets/c5ef8c6c-21e9-4065-9f79-d2165446a0b8)

<ul>
  <li>Save the script as <code>CreateUsers.ps1</code>.</li>
  <li>Click <strong>Run Script</strong> or press <code>F5</code> to execute it.</li>
  <li>Observe the accounts being created in <strong>Active Directory Users and Computers (ADUC)</strong>.</li>
</ul>

<h3>Step 4: Attempt to Log into Client-1</h3>

<ul>
  <li>Switch to <strong>Client-1</strong> and restart it.</li>
  <li>On the login screen, click <strong>Other User</strong>.</li>
  <li>Enter one of the newly created usernames:</li>
  <ul>
    <li><strong>Username:</strong> <code>mydomain.com\john.smith</code></li>
    <li><strong>Password:</strong> <code>Cyberlab123!</code></li>
  </ul>
  <li>Click <strong>Enter</strong> and verify successful login.</li>
</ul>

<h3>Finishing Up</h3>

<p>
By creating multiple users and testing logins, we confirm that authentication works properly within the domain. You can now manage these users from <strong>Active Directory Users and Computers (ADUC)</strong> on DC-1.
</p>

























        
<br />
