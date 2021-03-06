---
layout: page
title: "Q160158: Err Msg: Invalid Page Fault in Module Wininet.dll"
permalink: /kb/160/Q160158/
---

## Q160158: Err Msg: Invalid Page Fault in Module Wininet.dll

{% raw %}

	Article: Q160158
	Product(s): The Microsoft Network
	Version(s): 2.5,2.51,2.52,2.6,3.0,3.01,3.02,4.0,4.01,4.01 Service Pack 1,4.01 Service Pack 2,5
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbmsn
	Last Modified: 16-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network versions 2.5, 2.51, 2.52, 2.6 
	- Microsoft Internet Explorer versions 3.0, 3.01, 3.02, 4.0, 4.01, 4.01 Service Pack 1, 4.01 Service Pack 2, 5 for Windows 95 
	- the operating system: Microsoft Windows 95 
	- the operating system: Microsoft Windows 98 
	- the operating system: Microsoft Windows 98 Second Edition 
	- Microsoft Internet Explorer versions 4.0, 4.01, 4.01 Service Pack 1, 4.01 Service Pack 2, 5 for Windows 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	While you are using MSN, The Microsoft Network, or Microsoft Internet Explorer,
	you may receive an error message similar to one of the following messages:
	
	  
	
	- Iexplore caused an invalid page fault in module Wininet.dll.
	
	- Msnviewr caused an invalid page fault in module Wininet.dll.
	
	- The Urlmon.dll file is linked to the missing export file Wininet.dll.
	
	- Iexplore caused a divide error in module Wininet.dll.
	
	- Msnviewr caused a divide error in module Wininet.dll.
	
	- IExplore caused exception c0000006h in Wininet.dll
	
	CAUSE
	=====
	
	This behavior can occur for one of the following reasons:
	
	- One or more cache files in the Temporary Internet Files folder may be
	  damaged.
	
	- The History folder or the cache folders used by Internet Explorer are
	  damaged.
	
	- The index files used to track the contents of the History or cache folders
	  are damaged.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods:
	
	Method 1
	--------
	
	Delete the Temporary Internet Files folder. To do so, follow these steps:
	
	1. Click Start, point to Programs, and then click MS-DOS Prompt.
	
	2. Type deltree tempor~1, and then press ENTER. When you are prompted to confirm
	  the deletion, press Y, and then press ENTER.
	
	3. Type exit, and then press ENTER.
	
	4. Click the Internet Explorer icon and the necessary folders will be re-built
	  upon starting.
	
	If the issue continues to occur, proceed to the next method.
	
	Method 2
	--------
	
	Empty the History and cache folders used by Internet Explorer. To do so, follow
	these steps:
	
	1. Click Options on the View menu in Internet Explorer.
	
	2. Click the Navigation tab, click Clear History in the History area, and then
	  click Yes in the dialog box that appears.
	
	3. Click the Advanced tab, click Settings in the Temporary Internet Files area,
	  click Empty Folder, and then click Yes in the dialog box that appears.
	
	NOTE: After performing these steps, check to see if the issue has been resolved.
	If it has not been resolved, continue with step 4.
	
	4. In Control Panel, double-click Add/Remove Programs.
	
	5. Click Internet Explorer in the list of installed programs, and then click
	  Add/Remove.
	
	6. After Internet Explorer has been removed, restart the computer. When you see
	  the "Starting Windows 95" message, press the F8 key, and then choose Command
	  Prompt Only from the Startup menu.
	
	7. Type the following commands, pressing ENTER after each command.
	
	  NOTE: When you press ENTER after typing each of the following deltree
	  commands, you should be prompted to confirm that you want to delete the
	  folder. If this prompt is not displayed, the deltree command may have been
	  typed incorrectly.
	
	        cd \windows
	        smartdrv
	        deltree tempor~1
	        deltree history
	        cd system
	        ren mshtml.dll mshtml.old
	        ren shdocvw.dll shdocvw.old
	        ren inetcfg.dll inetcfg.old
	        ren actxprxy.dll actxprxy.old
	        ren wininet.dll wininet.old
	        ren cachevu.dll cachevu.old
	        ren inetcpl.cpl inetcpl.old
	        ren shlwapi.dll shlwapi.old
	        ren url.dll url.old
	        ren urlmon.dll urlmon.old
	        ren wsock32n.dll wsock32n.old
	
	8. Press the CTRL+ALT+DELETE key combination to restart your computer and
	  restart Windows normally.
	
	9. Reinstall Internet Explorer from your MSN CD.
	
	Additional query words: msnet msnetwork msiew95 w_money 2.00 2.50 2.60
	
	======================================================================
	Keywords          : kbenv kberrmsg kbmsn 
	Technology        : kbOSWin98 kbOSWin95 kbIEsearch kbOSWin98SE kbOSWinSearch kbMSNSearch kbIE95Search kbIE500Search kbZNotKeyword3 kbIE98Search kbIE300Win95 kbIE301Win95 kbIE302Win95 kbIE400Win95 kbIE401Win95 kbIE401Win95SP1 kbIE401Win95SP2 kbIE500Win95 kbIE400Win98 kbIE401Win98 kbIE401Win98SP1 kbIE401Win98SP2 kbIE500Win98 kbMSN252 kbMSN251 kbMSN260 kbMSN250
	Version           : :2.5,2.51,2.52,2.6,3.0,3.01,3.02,4.0,4.01,4.01 Service Pack 1,4.01 Service Pack 2,5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
