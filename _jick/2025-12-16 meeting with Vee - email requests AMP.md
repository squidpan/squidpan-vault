---
categories:
  - "[[Meetings]]"
type: []
date: 2025-12-16
org:
loc:
people:
  - "[[Vee Woo]]"
topics:
  - "[[Onboarding]]"
tags:
  - pulsedata
---
# Summary
---
First overview from Vee on current email request process (e.g. BST) and discussed terminology
1. Source/Custodian codes (e..g BST for JPMorgan chase)
2. Client/manager codes (e..g SGA for sage)
3. Account number
4. Custodian Contact ( 3rd party)
5. Manager Contacts (e.g. Sage. figured out from email addresses in the email)
6. Feed: e.g. connection via sftp
7. RM’s (Relationship Manager aka Contact at the Custodian)  info not currently available
8. AMP = Account Management Portal for Tickets (which feeds into DOTS). Internal only.
9. Dashboard is what clients to see file statues, tickets statuses, Account Numbers, File names.

Once a ticket is manually created from contents of email sent by clients they are sent to DOTS, Dashboard
# Next steps
---
- [ ] next time, need to categorize top 10 email clients and document their the completeness of their email requests id what's good and bad
- [ ] also need to understand dev side of effort: are you looking for requirements for the dev team to use as basis for development/testing?
- [ ] who are the developers?
- [ ] Vee sent me an example of good email request (FW: Reynders (RMC) - Add Account to Goulston & Storrs Master Feed Sample of a good email. )

# Good email
---
## Reynders (RMC) - Add Account to Goulston & Storrs Master Feed Sample of a good email
> [!info-good email]-
> On Mon, Sep 8, 2025 at 10:15 AM Miguel Sanchez <[miguel.sanchez@ridgelineapps.com](mailto:miguel.sanchez@ridgelineapps.com "mailto:miguel.sanchez@ridgelineapps.com")> wrote:
Hello, 
Please add the following account to Reynders McVeigh's Goulston Electra Feed:  
Manager: Reynders McVeigh Capital Management/ Ridgeline (RMC)
Custodian: Goulston & Storrs Master Feed  
Source Code: GSS-MTR
Account: 
332910999
332514000
332515000
302735000
334407000
Thank you, 
Miguel Sanchez
Sr. Customer Support Technical Analyst 
Ridgeline Apps
# Dashboard exports
---
- csv export files Sage (SGA) from DOTS-prod  (Dashboard reports (Tickets and Detail Accounts)
	- Electra Data (17) = Tickets for SAGE
	- Electra Data (18) = Accounts /Details for SAGE
		

Press `Enter` [^1]

````
	code block indented tab
    indented  4 spaces
````





[^1]: this is reference to using backtickse

