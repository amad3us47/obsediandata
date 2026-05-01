

I registered an account with the email address, thus the server will respond with `{"inReset":true}`, which means that the address is in use.
    
Now resend the request again, but with an invalid address like "[foobar123@internetwache.org](mailto:foobar123@internetwache.org)". The application will tell use the following: `{"error":"invalid_email_address"}`.



https://hackerone.com/reports/5688 - <span style="color:rgb(0, 176, 80)">19 May 2014</span> 