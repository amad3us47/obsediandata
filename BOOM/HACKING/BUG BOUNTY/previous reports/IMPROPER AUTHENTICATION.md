WORKING
        When a request with an invalid authenticity_token is received, the user is logged out (tested for updating user's profile, which is available here: [https://hackerone.com/diekatze/profile/edit](https://hackerone.com/diekatze/profile/edit)) and the user receives a new session cookie, which is not authenticated at this point. However, the authenticated session cookie used by a user before logging out is still active.


POC 
   1. 1

more links
1. https://medium.com/@KumarHalder/session-based-authentication-cookie-06a5f84c4c6b
2. https://hbothra22.medium.com/got-cookies-cookie-based-authentication-vulnerabilities-in-wild-55fa7c374be0
3. https://owasp.org/www-project-mobile-top-10/2014-risks/m9-improper-session-handling
4. https://allaboutcookies.org/types-of-cookies
5. https://brightsec.com/blog/broken-authentication-impact-examples-and-how-to-fix-it/
6. https://www.onelogin.com/blog/defending-your-organization-against-session-cookie-replay-attacks
7. https://cwe.mitre.org/data/definitions/287.html

https://hackerone.com/reports/737 - <span style="color:rgb(0, 176, 80)"> 19 Feb 2014</span> 