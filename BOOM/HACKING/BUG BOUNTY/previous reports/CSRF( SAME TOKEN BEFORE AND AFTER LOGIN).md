
I found that you are using X/Csrf token as a protection against CSRF attacks.

But you are using same X/Csrf token in and out.

eg z3qrwilV8lz7CXsMhmvqxn+93GDZm/m9w/d5DZjoj8w=

This token is same before and after log-in. This must be patch as it me result session hacks.


POC
1. https://www.youtube.com/watch?v=a50KnjgUusc



https://hackerone.com/reports/13639 - <span style="color:rgb(0, 176, 80)">30 May 2014</span> 