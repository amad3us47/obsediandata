

Your web application generates XSRF token values inside cookies which is not a best practice for web applications as revelation of cookies can reveal XSRF Tokens as well. Authenticity tokens should be kept separate from cookies and should be isolated to change operations in the account only.



https://hackerone.com/reports/2427 - <span style="color:rgb(0, 176, 80)">20 Apr 2014</span>


more
1. https://koumudi-garikipati.medium.com/why-a-csrf-token-shouldnt-be-passed-in-a-cookie-dd1d10d07332
2. 