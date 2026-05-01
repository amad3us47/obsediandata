
[@hussain](https://hackerone.com/hussain) reported a content spoofing and local redirect issue in Mapbox Studio in February 2016. Strings passed to the `message` query string parameter on requests to `https://www.mapbox.com/studio/forbidden/` would write text directly to the page.

[@hussain](https://hackerone.com/hussain) combined the content spoofing issue with a redirect via the `redirect` query string parameter. We were not able to reproduce an open redirect, though a local redirect to other pages within Studio did exist. We were also not able to replicate the injection of CSS in Internet Explorer and Mozilla Firefox that [@hussain](https://hackerone.com/hussain) reported.



https://hackerone.com/reports/114529  - <span style="color:rgb(0, 176, 80)">20 Apr 2016</span> 