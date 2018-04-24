## Fixing the UX disaster of Firefox right click contextual menus

#### More features = More better
Firefox seems to fall for this user interace trap *a lot* - modal contextual menus are packed with all kinds of options, all of which change based on the context of the right click. 

The no-context (ie anywhere on the page) right-click menu is the worst offender by far, packing in *four* redundant navigation controls into one menu item line, before adding all other contols already available in the tab controls. The problem is that about 99% percent of contextual menu interaction is in the form of right clicking a link to open in a new tab (assuming your other hand isn't near the keyboard) and if you happen to move the mouse outside the link boundry while clicking to open the menu, you'll invariably end up navigating the page forward or backward or maybe refreshing the page. Worse yet, since your original interaction mode (open link in new tab) wasn't dependent on how far to the right in the menu your are, the accidental navigation action will be more or less random. Random things make for terrible UX.  

![link context menu](https://raw.githubusercontent.com/pavelmalik/FirefoxRightClickMenus/master/link.png)

versus

![no context menu](https://raw.githubusercontent.com/pavelmalik/FirefoxRightClickMenus/master/page.png)


#### Simple Menu Wizard to the rescue
There is a great github project to fix all of that:
https://github.com/stonecrusher/simpleMenuWizard

Grab a copy the project, extract it into "chrome" folder in the  firefox profile (on MacOS you'll be looking for something like "/Users/YOURUSERNAME/Library/Application Support/Firefox/Profiles/RANDOMASCII.default/chrome/") and edit the following files:

blank-context.css
````
/*AGENT_SHEET*/

/*********************************************************************************************
  simpleMenuWizard: Firefox 57+ userChrome.css tweaks to remove context menu items.
  https://github.com/stonecrusher/simpleMenuWizard
**********************************************************************************************

/*** blank-context.css ***/

#context-navigation,                         /* Hide whole navigation bar            */
#context-back,                                 /* Navi: Back arrow                     */
#context-forward,                              /* Navi: Forward arrow                  */
#context-reload,                               /* Navi: Reload icon - 
                                                       combined position with stop icon   */
#context-stop,                                 /* Navi: Stop icon (x) - 
                                                       combined position with reload icon */
#context-bookmarkpage,                         /* Navi: Bookmark star icon             */
/* #context-sep-navigation,                     /************** Separator ***************/
#context-savepage,                           /* Save Page As...                      */
#context-pocket,                             /* Save Page to Pocket                  */
#context-sep-sendpagetodevice,               /************** Separator ***************/
#context-sendpagetodevice,                   /* Send Page to Device                  */
/* #context-sep-viewbgimage,                    /************** Separator ***************/
/* #context-viewbgimage,                        /* View Background Image                */
#context-selectall,                          /* Select All                           */
/* #context-context-sep-viewsource,             /************** Separator ***************/
/* #context-viewsource,                         /* View Page Source                     */
/* #context-viewinfo,                           /* View Page Info                       */
/* #inspect-separator,                          /************** Separator ***************/
/* #context-inspect,                            /* Inspect Element (Q)                  */
/* #screenshots_mozilla_org_create-screenshot,  /* Take a Screenshot                    */

#leave_this_dummy_here
    { display:none !important; }

````

link-context.css 
````
/*AGENT_SHEET*/

/*********************************************************************************************
  simpleMenuWizard: Firefox 57+ userChrome.css tweaks to remove context menu items.
  https://github.com/stonecrusher/simpleMenuWizard
**********************************************************************************************

/*** link-context.css ***/

/* #context-openlinkintab,               /* Open Link in New Tab             */
/* #context-openlinkinusercontext-menu,  /* Open Link in New Container Tab   */
/* #context-openlink,                    /* Open Link in New Window          */
/* #context-openlinkprivate,             /* Open Link in New Private Window  */
/* #context-sep-open,                    /************ Separator *************/
#context-bookmarklink,                /* Bookmark This Link               */
#context-savelink,                    /* Save Link As...                  */
#context-savelinktopocket,            /* Save Link to Pocket              */
/* #context-copylink,                    /* Copy Link Location               */
#context-searchselect,                /* Search [Google] for "[selected]" */
/* #context-sep-sendlinktodevice,        /************ Separator *************/
#context-sendlinktodevice,            /* Send Link to Device              */
/* #inspect-separator,                   /************ Separator *************/
/* #context-inspect,                     /* Inspect Element (Q)              */

#leave_this_dummy_here
    { display:none !important; }
````

The end results look like this
![no context fixed](https://raw.githubusercontent.com/pavelmalik/FirefoxRightClickMenus/master/fixed.png)
![link context fixed](https://raw.githubusercontent.com/pavelmalik/FirefoxRightClickMenus/master/fixedlink.png)



