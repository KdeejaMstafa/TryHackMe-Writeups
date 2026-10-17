<h1 align="center">Entra ID Monitoring</h1>
<h2>Task 2 — Password-Based Attacks</h2>
Stolen credentials are cheap. Credential-dumping sites and breach databases provide attackers with ready-made lists of real usernames and passwords. Many of these credentials are tied to active corporate accounts where users have reused passwords from personal services.

Entra ID is an especially attractive target because its authentication endpoints are internet-exposed by design. 
Any attacker with a username list can start attempting logins without ever touching the target's network perimeter. 
And when a login succeeds, it can look identical to a legitimate one, with no exploit, no malware, and no network anomalies. 
The only way to catch it is through log analysis.  
<b>Password Spraying</b>  
The attacker tries a small set of common passwords against many accounts. The goal is to stay under the lockout thresholds. Lockout thresholds are protection policies that lock accounts after reaching a pre-defined number of failed attempts. When a user is locked, they can't access their account until an admin or a defined timeout unlocks the account.
For example, if the policy is set to lock the account after 10 failed attempts, the attacker never exceeds 5 per account to stay stealthy. The volume is spread across accounts rather than concentrated in a single account.  
How it looks in logs:  
- Many failed sign-ins from the same IP address.
- Failures spread across multiple different usernames.
- All attempts occur within a short time window.

<b>Brute Force</b>  
On the other hand, in brute-force attacks, the attacker tries many passwords against a single account. This technique is less common against Entra ID due to the lockout policies. However, attackers can bypass this by throttling their attempts and spreading them over a long period, so they never exceed the lockout threshold.
For example, an attacker might try just one password per hour against the same account. This keeps the noise low enough to avoid triggering a lockout, making it slow and harder to detect because the attempts may span a longer time window.   
How it looks in logs:  
- Many failed sign-ins against a single username.
- High volume of attempts from a single IP or a small number of IPs.

<br>
<b>Questions</b>  

Q1: Which IP address is performing a password spraying?  
Answer: <code>94.20.222.248</code>  

Q2: Which IP address is performing a throttling brute force?  
Answer: <code>38.165.231.218</code>  

Q3: What is the user's email address that was compromised?  
Answer: <code>amanda.costa@finegalo.thm</code>
