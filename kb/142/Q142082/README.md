---
layout: page
title: "Q142082: FIX: CTL3D32.DLL Errors with Windows 95"
permalink: /kb/142/Q142082/
---

## Q142082: FIX: CTL3D32.DLL Errors with Windows 95

{% raw %}

	Article: Q142082
	Product(s): Microsoft FoxPro
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300bFIX
	Last Modified: 28-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After installing Visual FoxPro 3.0 under Windows 95, the following error may
	occur:
	
	  This application uses CTL3D32.DLL, which is not the correct version. This
	  version of CTL3D32.DLL is designated only for Windows NT systems.
	
	CAUSE
	=====
	
	This does not occur with all Windows 95 installations. At this time, Microsoft
	has not isolated a cause for this problem, but it is suspected that certain
	system configurations, combined with Visual FoxPro, cause confusion.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been corrected in version 3.0b.
	The easiest workaround is to expand the file in question from the cab file on
	the disk. For example, if the Visual FoxPro CD is in drive D, the command would
	be:
	
	     EXTRACT D:\VFP9.CAB /L C:\WINDOWS\SYSTEM\CTL3D32.DLL
	
	Additional query words: CTL3D32 DLL
	
	======================================================================
	Keywords          : kbvfp kbvfp300bFIX 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : 3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
