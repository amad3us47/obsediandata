
this bug allows a user to be logged in as the attacker. The main reason is that no state is maintained in the authentication flow. Although the Twitter flow still uses OAuth 1.0A, which has no state parameter as in OAuth 2, it is still possible to prevent this type of attack by setting an additional parameter in the oauth_callback value.


POC
1. https://www.youtube.com/watch?v=EG9gU5-UBAE
2. https://www.youtube.com/watch?v=O13xCKbe2IE
3. https://www.youtube.com/watch?v=ancD-ETB-mw
4. https://www.youtube.com/watch?v=PQTfFXmbPKQ
5. https://www.youtube.com/watch?v=J3QOZPJvcvg
6. https://www.youtube.com/watch?v=6AWrNvN-hcM
7. https://www.youtube.com/watch?v=CmG01xprrlU



https://hackerone.com/reports/13555 - <span style="color:rgb(0, 176, 80)">5 July 2014</span> 

more 
1. https://medium.com/@oXnoOneXo/csrf-in-oauth-flow-of-a-private-program-46db275eed33
2. https://auth0.com/blog/prevent-csrf-attacks-in-oauth-2-implementations/
3. https://medium.com/@cyberpro151/oauth-csrf-exploiting-the-authorization-code-flow-for-account-takeover-f67cee914d39
4. 