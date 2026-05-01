
We can create posts under [https://subdomain.slack.com/files/create/post](https://subdomain.slack.com/files/create/post)

Post will have XSS payload like "><img src=x onerror=alert(10);> in title and body

We save it and hit "Create public link" and once we share the link it will trigger XSS.


https://hackerone.com/reports/2617 - <span style="color:rgb(0, 176, 80)">23 May 2014</span> 