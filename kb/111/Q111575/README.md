---
layout: page
title: "Q111575: Security Settings File Error with Shared Windows Installation"
permalink: /kb/111/Q111575/
---

## Q111575: Security Settings File Error with Shared Windows Installation

{% raw %}

	Article: Q111575
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you used SETUP /N to set up a shared copy of Microsoft Windows for Workgroups
	version 3.11 and you have Novell NetWare installed as an additional network, you
	may receive one of the following error messages when you use the NET command:
	
	  Error reading security-settings file.
	
	-or-
	
	  Error 2: The specified file was not found. An error occurred accessing the
	  security settings file.
	
	CAUSE
	=====
	
	These errors occur when your NetWare search path has the shared Windows
	directory before your local Windows directory, or your current directory is the
	shared Windows directory.
	
	In both cases, Windows for Workgroups is finding a security settings file that is
	not valid for your system.
	
	WORKAROUND
	==========
	
	To work around this problem, change your search path so your local Windows
	directory is listed before your shared Windows directory, or change your current
	directory to something other than the shared Windows directory.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Windows for Workgroups
	version 3.11. We are researching this problem and will post new information here
	as it becomes available.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : WINDOWS:3.11
	
	=============================================================================
	

{% endraw %}
