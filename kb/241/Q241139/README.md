---
layout: page
title: "Q241139: TPU: Collaboration Data Objects Required to Install TPU"
permalink: /kb/241/Q241139/
---

## Q241139: TPU: Collaboration Data Objects Required to Install TPU

{% raw %}

	Article: Q241139
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.5
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup kbtool
	Last Modified: 22-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft BackOffice Server 4.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to install the Team Productivity Update (TPU), you may receive the
	following error message in TPUSetup:
	
	  Microsoft Outlook 2000 Team Folders Wizard requires Outlook 2000 installed
	  with Collaboration Data Objects component.
	
	CAUSE
	=====
	
	This error message can occur you do not have Collaborative Data Objects
	installed on the server.
	
	RESOLUTION
	==========
	
	To resolve this issue, install Collaborative Data Objects on the server after
	you install Outlook 2000. To install Outlook 2000, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click the Services icon, click Microsoft Exchange System Attendant,
	  and then click Stop. If you are prompted, click OK to stop the rest of the
	  Exchange services.
	
	3. Start Outlook 2000 Setup.
	
	4. Type in your user information and CD-Key, and then click Next.
	
	5. Accept the License Agreement, click Next, and then click Customize.
	
	6. Click the location where you want to install Outlook 2000.
	
	7. In the Outlook 2000 installation tree, click the "X" next to Collaborative
	  Data Objects.
	
	8. Click to use the "Run from My Computer" option.
	
	9. Click Install Now.
	
	To install Collaborative Data Objects, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click the Services icon, click Microsoft Exchange System Attendant,
	  and then click Stop. If you are prompted, click OK to stop the rest of the
	  Exchange services.
	
	3. Close the Microsoft Exchange System Attendant tool.
	
	4. Double-click Add/Remove Programs.
	
	5. Click Outlook 2000m and then click Add/Remove.
	
	6. Click "Add or Remove Features."
	
	7. Under "Microsoft Outlook for Windows," click "Run from My Computer."
	
	8. Click Update Now.
	
	MORE INFORMATION
	================
	
	Outlook 2000 requires the Collaborative Data Objects component to install the
	Team Productivity Update program. For more information about minimum
	requirements and setup procedures, see the Installation.htm and Readme.htm files
	contained on the TPU CD-ROM.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbsetup kbtool 
	Technology        : kbAudDeveloper kbBackOfficeSearch kbBackOfficeServ450
	Version           : winnt:4.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
