# <div align="center">Overheard at Breakfast</div>

### Concierge Briefing
The breakfast terrace is loud this morning, clinking cutlery, espresso machines, the usual chatter. One guest couldn't help but linger at a nearby table, seeing more of a conversation than they were meant to.
When the table's occupant stepped away for a refill, they seized the moment and grabbed a screenshot before it could disappear. Somewhere in that conversation is enough to track down an account nobody was supposed to find.
### Itinerary
 
◻ Analyze the provided conversation for identifying details
 
◻ Extract the relevant clues
 
◻ Locate the hidden account
 
◻ Submit the flag
<br>

<b>@0xMia's STORY —— </b> "the breakfast crowd really said the quiet part out loud this morning 😭 y'all need to actually READ what they said, not just skim it #HackerHolidays"

### Hunting The Flag
In the given screenshot, there were two prominent clues.  <img width="1175" height="781" alt="conversation" src="https://github.com/user-attachments/assets/34db5eb1-3a84-4988-9833-12381b350e21" />
<br>

1. The tool that lets Lambo upload their profile and link other social media accounts starts with the letter G.
2. Lambo's Gmail account is lambobytelotushotel@gmail.com.  

I used **EmailOSINT**(emailosint.org)</u> to gather details about the gmail address. Here's what I found:  

<img width="1548" height="501" alt="emailOSINT-AI-summary" src="https://github.com/user-attachments/assets/fd04ae30-4037-4768-a21b-b9a4a8c77689" />  
<img width="954" height="856" alt="emailOSINT-details" src="https://github.com/user-attachments/assets/797707bd-bc1e-485f-a165-f3ec0a7ea592" />   

The tool starting with G was Gravatar and after clicking the link to Lambo's account I received an base64-encoded string: VEhNe1MzY3JlVF9QcjBmaWwzX0g0c19iMzNuX0lkZW50MWZpM2R9  
<br>
After decoding it via CyberChef, I found the flag: THM{S3creT_Pr0fil3_H4s_b33n_Ident1fi3d}
<br>
<br>
<p align="center">✧ ─ ✦ ─ ✧ ─ ✦ ─ ✧  THE END  ✧ ─ ✦ ─ ✧ ─ ✦ ─ ✧</p>
