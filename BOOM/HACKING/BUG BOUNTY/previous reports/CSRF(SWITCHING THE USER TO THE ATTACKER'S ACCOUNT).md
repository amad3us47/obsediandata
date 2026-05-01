WORKING 
        Attacker sets up an account and goes to [https://hackerone.com/users/password/new](https://hackerone.com/users/password/new) to remind a password for this account. Then a link with a password reset token is sent to the attacker's e-mail. Now the attacker knows everything to prepare the aforementioned Request2 (ENTER_HERE_RESET_PASSWORD_TOKEN_FROM_MAIL - a password reset token from the e-mail; ENTER_HERE_NEW_PASSWORD - just enter new password for the attacker's account).Request2 sets a new password for the attacker's account and allows the attacker to log in the user to this account. When the user is already logged in, Request1 needs to be sent first to log out the user.

POC


https://hackerone.com/reports/727

more links
1. https://cyberbull.medium.com/cross-site-request-forgery-csrf-%EF%B8%8F-deep-dive-f4ff8bb7d596
2. https://brightsec.com/blog/csrf-example/
3. 



