
Steps to repro: 1) Create a HackerOne account having email address "[a@x.com](mailto:a@x.com)". 
2) Now Logout and ask for password reset link. Don't use the password reset link. 
3) Login using the same password back and update your email address to "[b@x.com](mailto:b@x.com)" and verify the same. 
4) Now logout and use the password reset link which was mailed to "[a@x.com](mailto:a@x.com)" in step 2.
5) Password will be changed.

All previous password reset links should automatically expire once a user changes his email address.


https://hackerone.com/reports/17383 - <span style="color:rgb(0, 176, 80)">26 July 2014</span> 