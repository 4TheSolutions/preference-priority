The A2 cell should look like `Event 0: Members [306645, 110137, 153380, 110452, 119273, 125495]` with some IDs. 

In column C, use `=REGEXREPLACE(A2, "[^,[0-9]", "")` to get rid of excess, then in column D use `=RIGHT(C2,LEN(C2)-2)` for the first 10 rows and `=RIGHT(C2,LEN(C2)-3)` to account for the two digits in the event quantifiers. 

In column E, use `=SPLIT(D2,",")` to split the IDs into columns. Finally in column O, drag down the numbers 0, 1, 2, ... until all the events' quantifiers are attached to each row. 
