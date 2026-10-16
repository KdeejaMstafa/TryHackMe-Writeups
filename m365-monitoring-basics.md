<h1 align="center">M365 Monitoring Basics</h1>

<h2>Task 2 — What are Identity Providers</h2>
<h3><b>What is an Identity?</b></h3>

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
<b>Questions</b>

Q1: What authentication resource can prevent attackers from authenticating with only a stolen password?  
Answer: <code>MFA</code>  
Q2: What can help us detect and monitor cloud identity threats?  
Answer: <code>Logs</code>  

<h2>Task 4 — Entra ID Sign-in Logs</h2>
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
<b>Questions</b>

Q1: What was the first change made by the attacker in the compromised user account?  
Answer Format: Paste the exact value of <b>activityDisplayName</b>  
Answer: <code>User started security info registration</code>  
Q2: What is the <b>activityDisplayName</b> that reveals all the details of the modified properties in a user?  
Answer: <code>Update user</code>  
Q3: What is the second change made in the account?  
Answer Format: Paste the exact value of the <b>activityDisplayName</b> field.  
Answer: <code>Reset password (self-service)</code>
