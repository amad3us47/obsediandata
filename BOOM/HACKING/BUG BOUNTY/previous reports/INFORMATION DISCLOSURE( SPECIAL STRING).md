
When I go to /index.php/dashboard/pages/types?ctID[]=4&task=edit I get thrown the following : `mysqlt error: [1054: Unknown column 'Array' in 'where clause'] in EXECUTE("SELECT PageTypes.ctID, ComposerTypes.ctID as ctIDc, ctHandle, ctIsInternal, ctName, ctIcon, pkgID, ctComposerPublishPageMethod, ctComposerPublishPageTypeID, ctComposerPublishPageParentID from PageTypes left join ComposerTypes on PageTypes.ctID = ComposerTypes.ctID where PageTypes.ctID = Array")`



https://hackerone.com/reports/4811 - <span style="color:rgb(0, 176, 80)">9 June 2014</span> 