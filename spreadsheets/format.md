Continue working in the "zoo" sheet. In coluumn P, use `=xlookup(O2,events!B:B,events!A:A)`to match quantifier to event. 

In **column Q**, use `=IF(xlookup(E2,'data'!$B:$B,'data'!$G:$G) = "NA",xlookup(E2,'data'!$B:$B,'data'!$A:$A),xlookup(E2,'data'!$B:$B,'data'!$G:$G))`. This checks whether a competitor is individual or in a team, and pulls the data accordingly. This should be copy pasted ($ signs maintain the columns while the E will shift right based on pasted location) in **columns R, S, T, U, V, W, X, Y, Z**. 

The event assignments are complete. 
