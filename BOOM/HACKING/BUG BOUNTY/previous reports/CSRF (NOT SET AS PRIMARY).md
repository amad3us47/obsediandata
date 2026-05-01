
On navigating to the Accounts page, a Coinbase user can create multiple accounts. The user can then make any of these accounts as their primary account. There are also other options of renaming and deleting these accounts.

Although there is a CSRF token being sent as a POST parameter for the delete operation, there is no such CSRF token for the "set as primary" operation. Infact, this request is a GET request. Similar CSRF controls should be implemented for the "Set as primary" operation as well.



https://hackerone.com/reports/10563 - <span style="color:rgb(0, 176, 80)">26 July 2014</span> 