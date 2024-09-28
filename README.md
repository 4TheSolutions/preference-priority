# Preference-Priority Assignments
Initially made for Westwood DECA's event selection process

The **raw input** is generated from the form with the following contents:
- Full Legal Name (First & Last) [One string]
- Student ID [6 digits]
- Past DECA performance, select the highest honor you've received. [6 options: ICDC Top 20 (Finalists & Top Testers), ICDC Qualifier, State Finalist, State Qualifier, District Attendee, I'm a 1st year member!]
- First Competitive Event Preference [51 options]
- List your team member's full name AND your full name (ex: you, member A, member B). If you are competing solo, please type "NA". [One string]
- Second Competitive Event Preference [51 options]
- List your team member's full name AND your full name (ex: you, member A, member B). If you are competing solo, please type "NA". [One string]
- Third Competitive Event Preference [51 options]
- List your team member's full name AND your full name (ex: you, member A, member B). If you are competing solo, please type "NA". [One string]
- Any notes?
Note that it should be required that members either choose ONLY solo competitive events or choose events with the SAME EXACT TEAM. 

The form links to a spreadsheet, call it "data". Delete the timestamp column, and edit the sheet as follows:
- Column A: Full Legal Name
- Column B: Student ID
- Column C: Past DECA performance
- Column D: Quantified Past DECA performance.
- Column E: First Competitive Event Preference
- Column F: Quantified First Competitive Event Preference
- Column G: Team member's full name and your full name.
- Column H: Regex rearranged column G.
- Column I: Second Competitive Event Preference
- Column J: Quantified Second Competitive Event Preference
- Column K: Team member's full name and your full name.
- Column L: Third Competitive Event Preference
- Column M: Quantified Third Competitive Event Preference
- Column N: Team member's full name and your full name.
- Column O: Preferences dictionary
- Column P: Priority dictionary

**Column D, F, H, J, M, O, P** must be added onto the existing spreadsheet. First, to quantify competitive events, create a separate tab with the following data, call it "events": 
```
Accounting Applications (ACT)	0
Apparel and Accessories Marketing (AAM)	1
Automotive Services Marketing (ASM)	2
Business Finance (BFS)	3
Business Growth Plan (EBG)	4
Business Law and Ethics (BLTDM)	5
Business Services Marketing (BSM)	6
Business Services Operations (BOR)	7
Business Solutions Project (PMBS)	8
Buying and Merchandising (BTDM)	9
Buying and Merchandising Operations (BMOR)	10
Career Development Project (PMCD)	11
Community Awareness Project (PMCA)	12
Community Giving Project (PMCG)	13
Entrepreneurship (ENT)	14
Entrepreneurship (ETDM)	15
Finance Operations (FOR)	16
Financial Consulting (FCE)	17
Financial Literacy Project (PMFL)	18
Financial Services (FTDM)	19
Food Marketing (FMS)	20
Franchise Business Plan (EFB)	21
Hospitality and Tourism Operations (HTOR)	22
Hospitality and Tourism Professional Selling (HTPS)	23
Hospitality Services (HTDM)	24
Hotel and Lodging Management (HLM)	25
Human Resources Management (HRM)	26
Independent Business Plan (EIB)	27
Innovation Plan (EIP)	28
Integrated Marketing Campaign - Event (IMCE)	29
Integrated Marketing Campaign - Product (IMCP)	30
Integrated Marketing Campaign - Service (IMCS)	31
International Business Plan (IBP)	32
Marketing Communications (MCS)	33
Marketing Management (MTDM)	34
Personal Financial Literacy (PFL)	35
Principles of Business Management and Administration (PBM)	36
Principles of Entrepreneurship (PEN)	37
Principles of Finance (PFN)	38
Principles of Hospitality and Tourism (PHT)	39
Principles of Marketing (PMK)	40
Professional Selling (PSE)	41
Quick Serve Restaurant Management (QSRM)	42
Restaurant and Food Service Management (RFSM)	43
Retail Merchandising (RMS)	44
Sale Project (PMSP)	45
Sports and Entertainment Marketing (SEM)	46
Sports and Entertainment Marketing (STDM)	47
Sports and Entertainment Marketing Operations (SEOR)	48
Start-Up Business Plan (ESB)	49
Travel and Tourism (TTDM)	50
```

Create another tab with the following data, call it "priority":
```
District Attendee	1
I'm a 1st year member!	0
ICDC Qualifier	4
ICDC Top 20 (Finalists & Top Testers)	5
State Finalist	3
State Qualifier	2
```

In **column D**, input the formula: `=xlookup(C1,priority!A:A,priority!B:B)`. In **columns F, J, M**, input the formula: `=xlookup(E4,Sheet2!A:A,Sheet2!B:B)`, `=xlookup(I5,Sheet2!A:A,Sheet2!B:B)`, and `=xlookup(L5,Sheet2!A:A,Sheet2!B:B)`. In **columns O, P**, input the formula: `=CONCATENATE(B1," : [",F1,",",J1,",",M1,"],")` and `=CONCATENATE(B1," : ",D1,",")`. 

In **column H**, input the following regex formula: 
```
=ARRAYFORMULA(JOIN("", SORT(MID(LOWER(G1), SEQUENCE(LEN(G1)), 1))))
```
