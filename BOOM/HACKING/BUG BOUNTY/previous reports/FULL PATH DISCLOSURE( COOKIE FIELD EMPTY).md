

When you emtpy the cookie `CONCRETE5` it will throw the following error on the page :

`Warning: session_start() [function.session-start]: The session id contains illegal characters, valid characters are a-z, A-Z, 0-9 and '-,' in /home/c5host/msm_versions/012312/concrete/startup/session.php on line 22 Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /home/c5host/msm_versions/012312/concrete/startup/session.php:22) in /home/c5host/msm_versions/012312/concrete/startup/session.php on line 22` `Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /home/c5host/msm_versions/012312/concrete/startup/session.php:22) in /home/c5host/msm_versions/012312/concrete/startup/session.php on line 22 Warning: Cannot modify header information - headers already sent by (output started at /home/c5host/msm_versions/012312/concrete/startup/session.php:22) in /home/c5host/msm_versions/012312/concrete/libraries/view.php on line 841`



https://hackerone.com/reports/4931 - <span style="color:rgb(0, 176, 80)">9 June 2014</span> 

more 
1. https://0x80dotblog.wordpress.com/2021/07/25/triggering-full-path-disclosure-the-basics/
2. 