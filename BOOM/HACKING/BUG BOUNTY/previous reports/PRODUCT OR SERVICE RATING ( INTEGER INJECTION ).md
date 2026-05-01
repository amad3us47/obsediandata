
Authenticated user can register for some course (paid or free). After registering and taking couple of lectures "Rate course" functional becomes active.

Malicious user can fill the rating form and submit it. By intercepting request to the server's API (by using intercepting proxy tool) and modify rating value he can set enormously large values as rating. After experimenting following restrictions was found


https://hackerone.com/reports/73808 - <span style="color:rgb(0, 176, 80)">25 Sep 2015</span> 