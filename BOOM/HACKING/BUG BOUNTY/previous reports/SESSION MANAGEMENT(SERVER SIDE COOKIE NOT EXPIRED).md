

Hackerone fails to expire the session cookie from the server side even when the user logs off upon clicking "Sign-Out" from the application. The cookie is cleared from the client side (browser), but is not cleared from the server side. If reused, it provides access to the user's account. Upon logging in again, a new session cookie is created, but the old session cookies still stay active on the server side. Therefore, any session cookie can be reused to gain access to the user's account. 


https://hackerone.com/reports/288 - <span style="color:rgb(0, 176, 80)">19 Apr 2014
</span> 