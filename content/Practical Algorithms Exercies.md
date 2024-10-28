
1. Assign numerical value to first letter of surname based on what percentage of way through the alphabet it is e.g. m = 50%, b = 8%, etc...
2. Open the phone book the same percentage of the way through e.g. if there are 700 pages and surname begins with m, open at page 350
3. Is the first letter of the first name on the page the same as the first letter of the surname you're looking for? GO TO STEP: 4 ELSE GO TO STEP 11

4. Does the surname your looking for fall alphabetically before the first name on the page? GO TO STEP: 5 ELSE GO TO STEP 6
5. Go back one page, repeat step 3
6. Does the surname your looking for fall alphabetically before the last name on the page: GO TO STEP 7 ELSE GO TO STEP 9
7. Read the names on the page until you find the one you're looking for. The number will be next to it.
8. Required number is next to name. END.
9. Go forward one page
10. Does the surname your looking for fall alphabetically before the last name on the page? GO TO STEP 7 ELSE go to step 9.

11. If required letter is before current letter: discard pages after current page. Else discard pages before current page
12. Assign numerical value to required letter based on percentage of way through remaining alphabet before or after the current letter
13. Go to page the same percentage of way through pages on the required side e.g. if looking for m and opened at p on page 350, go to page 284
14. Repeat from step 3


ANALYSIS: Best case: 7 steps. Worst case: 7*(x/2?)+7*(y/2) [x: 1-N] (where y is number of pages of largest letter section)