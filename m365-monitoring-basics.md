<h1 align="center">M365 Monitoring Basics</h1>

<h2>Task 2 — What are Identity Providers</h2>
<h3>What is an Identity?</h3>

<div>
A digital identity is a set of attributes that uniquely represent an entity within a computer system. That entity can be a person, a device, or a software component. Identities are used to authenticate entities, authorize their access to resources, enable communication, and support actions such as accessing services or performing transactions.

At a high level, identities can be grouped into three categories:

<b>Human identities:</b> Represent people, such as employees, contractors, partners, or customers.<br>
<b>Workload identities:</b> Represent software components, including applications, services, scripts, or containers, that need to authenticate to other systems.<br>
<b>Device identities:</b> Represent physical devices like desktops, laptops, mobile phones, and IoT devices. These identities are separate from the humans who use them.
</div>
<div>An <b>Identity Provider (IdP)</b> is the system responsible for creating and managing these identities. 
It handles authentication (verifying identity), authorization (controlling access), and auditing by recording identity-related activity across connected services. Microsoft Entra ID is an example of a cloud-based identity provider. 
Other examples include Twitter, Google, Amazon, LinkedIn, and Apple.</div>
<br>
<b>Questions</b>

Q1: What type of application is Entra ID?  
Answer: <code>Identity Provider</code>  
Q2: What type of identity is a server account?  
Answer: <code>Device</code>  

<h2>Task 3 — Identities as the Target</h2>
<h3>Why Attackers Are Targeting Cloud Credentials</h3>
Attackers target cloud-based identity providers because they provide:

- <b>Remote access from anywhere:</b> Authentication occurs over the internet, so attackers don’t need access to the internal network.
- <b>Legitimate access to multiple services via SSO:</b> One successful sign-in can unlock emails, files, chat, and connected apps for a user.
- <b>Out of the radar of traditional tools:</b> Firewalls and endpoint tools may see nothing suspicious because the attacker is using valid credentials or the authentication is occurring outside of their visibility.
- <b>Direct access to high-value resources:</b> Email and collaboration platforms contain sensitive data, internal communication, and often allow resetting account credentials and other authentication factors.
  
Entra ID has plenty of features to better protect identities within a tenant and prevent attackers from being successful. This leads to another important question: “If Entra ID is so secure, how do these attacks still work?”
<br><br>
<b>Questions</b>  
Q1: What authentication resource can prevent attackers from authenticating with only a stolen password?  
Answer: <code>MFA</code>  
Q2: What can help us detect and monitor cloud identity threats?  
Answer: <code>Logs</code>  

<h2>Task 4 — Entra ID Sign-in Logs</h2>
<h3>Entra ID Core Components</h3>
Before we explore the logs, let's understand the key components that generate them:  
<b>Users and Sign-ins (Authentication)</b>  
Every time a user attempts to authenticate to any service protected by Entra ID, a record is created. This includes successful logins, failed attempts, MFA challenges, and the context around each event (IP address, location, device, application, and others).  

<b>Roles and Access Decisions (Authorization)</b>  
After authentication, Entra ID determines what the user is allowed to do based on their assigned roles and permissions. Changes to these roles, group memberships, or permissions are all logged in audit events.  

<b>Security Features</b>

Entra ID includes built-in security capabilities that generate their own logs:

- Multi-factor authentication (MFA): Logs show whether MFA was required, prompted, satisfied, or bypassed.  
- Conditional Access policies: These policies enforce rules like "require MFA from untrusted locations." Logs show which policies were applied and their outcomes (allowed, blocked, MFA required).  
- Identity Protection: Entra ID's native threat detection flags risky sign-ins (impossible travel, anonymous IP, password spray) and risky users. We won't dive deep into these in this room, but we will see how these logs can help us identify threats in the next room, Entra ID Monitoring.  


<b>Questions</b>  
Q1: What is the email address of the compromised identity?  
Answer: <code>allan.smith@finegalo.thm</code>  
Q2: What is the IP address used by the attacker?  
Answer: <code>2804:2488:7082:a4c0:fd97:b11b:9895:49c0</code>  
Q3: What is the city of the IP address used by the attacker?  
Answer: <code>Belo Horizonte</code>  
Q4: When was the first successful sign-in in the compromised account after the failure attempts?  
Answer Format: 1/12/25 1:15:00.000 PM (Exact Splunk <b>Time</b> value)   
Answer: <code>2/11/26 6:16:53.000 PM</code>  
Q5: What is the first application the attacker accessed after the office home page?  
Answer Format: The exact value of the <b>appDisplayName</b> field.  
Answer: <code>One Outlook Web</code>  

<h2>Task 5 — Entra ID Audit Logs</h2>
Audit logs capture administrative actions and changes made within the Entra ID environment. Below are some examples of post-compromise activities an attacker can perform, and you can hunt with logs:

- Resetting passwords to maintain access
- Adding new MFA methods or devices
- Assigning privileged roles to escalate access
- Modifying user attributes
- Registering malicious applications
<br>
<b>Questions</b>  

Q1: What was the first change made by the attacker in the compromised user account?  
Answer Format: Paste the exact value of <b>activityDisplayName</b>  
Answer: <code>User started security info registration</code>  
Q2: What is the <b>activityDisplayName</b> that reveals all the details of the modified properties in a user?  
Answer: <code>Update user</code>  
Q3: What is the second change made in the account?  
Answer Format: Paste the exact value of the <b>activityDisplayName</b> field.  
Answer: <code>Reset password (self-service)</code>

<h2>Task 6 — M365 Introduction</h2>
<div><h3>What is Microsoft 365?</h3>
Microsoft 365 (M365) is a collection of cloud-based productivity and collaboration services tied to Entra ID identities. Once a user authenticates through Entra ID, they gain access to services like:

<b>Exchange Online (Outlook):</b> Email, calendars, and mailbox management.  
<b>SharePoint Online:</b> Document storage, file sharing, and team sites.  
<b>OneDrive:</b> Personal cloud storage.  
<b>Teams:</b> Chat, meetings, and collaboration.  
<b>Other services:</b> Power BI, Dynamics, and various Microsoft apps.  </div>
<br>
<h2>Task 7 — M365 Audit Logs</h2>
<h3>Hunting for Post-Compromise M365 Activities</h3>
For your investigation into M365 logs, identifying suspicious activities on the compromised account is essential. You will further explore these attackers' techniques in this module. For now, here are some common post-compromise activities you should be aware of:  

Mailbox Manipulation:

- Creation of inbox rules to delete, forward, or move emails
- Mass email deletion or moves to the deleted items
- Emails sent to external addresses
- Access from unusual IP addresses or locations  

File Operations:

- Mass file downloads from SharePoint or OneDrive
- Access to sensitive or executive-level documents
- File sharing to external domains
- Downloads of files the user wouldn't normally access
<br>
<b>Questions</b>  

Q1: What is the application used by the attacker?  
Answer Format: Paste the exact value of the <b>Workload</b> field.  
Answer: <code>Exchange</code>  

Q2: What is the change made in the user application by the attacker?    
Answer Format: Paste the exact value of the <b>Operation</b> field.  
Answer: <code>New-InboxRule</code>  

Q3: What is the subject of the email message sent by the attacker?   
Answer: <code>URGENT: Approval for new internal VPN Access</code>  

Q4: When did the attacker access the response to the message?  
Answer Format: 1/12/25 1:15:00.000 PM  
(Exact Splunk <b>Time</b> value)  
Answer: <code>2/11/26 6:20:09.000 PM</code>  

Q5: Which path was the response stored in?  
Answer Format: \PathName  
Answer: <code>\Deleted Items</code>  
