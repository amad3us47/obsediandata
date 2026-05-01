
CSRFToken=[TOKEN]&requestInvitation[repositoryID]=[ID]

Here, suppose ID of last Project created on Localize is `9a` , now as localize application normally works, next ID will be `9b` .. (i can be wrong here) with Live HTTP Header, You can Send Requests to project that is not even created till now.. all you have to do is just change the ID parameter to `9b` `9c` `9d` `9e` `9f` more and more and send request. Now when Project with ID `9b` `9c` `9d` `9e` `9f` will get created, doesn't matter this project is `PUBLIC` or `PRIVATE` (because of that bug i reported earlier), there will be an "Invitation Request" awaiting for confirmation.



https://hackerone.com/reports/9088 - <span style="color:rgb(0, 176, 80)">23 Apr 2014</span> 