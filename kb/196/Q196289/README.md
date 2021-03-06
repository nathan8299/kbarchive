---
layout: page
title: "Q196289: PRB: SP3 Clients Cannot Change Passwords - Error C00000BE"
permalink: /kb/196/Q196289/
---

## Q196289: PRB: SP3 Clients Cannot Change Passwords - Error C00000BE

{% raw %}

	Article: Q196289
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If all of the following conditions are true, you may receive the following error
	message:
	
	  Unable to change password on this account (C00000BE).
	
	- The clients are Windows NT 4.0 with Service Pack 3
	
	- The domain controllers are Windows NT 4 with Service Pack 4
	
	- You are required to change your password the next time you log on (it has
	  expired or the administrator has selected the User Must Change Password at
	  Next Logon check box).
	
	- You have installed the Restrict Anonymous hotfix from Q143474.
	
	  For additional information about this hotfix, please see the following article
	  in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q143474
	  TITLE : Restricting Information Available to Anonymous Logon Users
	
	RESOLUTION
	==========
	
	To resolve this problem, update the clients to the latest service pack.
	
	MORE INFORMATION
	================
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0 Service
	Pack 3.
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
