---
layout: page
title: "Q157050: PRB: Loops of @..SAY &lt;General field&gt; Causes GPF"
permalink: /kb/157/Q157050/
---

## Q157050: PRB: Loops of @..SAY &lt;General field&gt; Causes GPF

{% raw %}

	Article: Q157050
	Product(s): Microsoft FoxPro
	Version(s): 3.00 3.00b 5.00
	Operating System(s): 
	Keyword(s): kberrmsg kbvfp300 kbvfp500 kbvfp600
	Last Modified: 29-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	WARNING: The information in this article has not been confirmed or tested by
	Microsoft. Some or all of the information in this article has been taken from
	unconfirmed customer reports. ANY USE BY YOU OF THE INFORMATION PROVIDED IN THIS
	ARTICLE IS AT YOUR OWN RISK. Microsoft provides this information "as is" without
	warranty of any kind, either expressed or implied, including but not limited to
	the implied warranties of merchantability and/or fitness for a particular
	purpose.
	
	Looping @...SAY <general field contain embedded pictures> might cause a
	General Protection Fault (GPF) in Windows 3.1 and Windows for Workgroups, and it
	might trigger one of the following error messages:
	
	  VFP caused an invalid page fault in module kernal32.dll at <address>"
	  under Windows 95
	
	  -or-
	
	  Application Error : Access violation : <address> under Winnt3.51
	
	WORKAROUND
	==========
	
	Instead of displaying a Picture from the general field, issue the following
	command:
	
	  
	
	  @...SAY <Picture File name> Bitmap
	
	STATUS
	======
	
	Microsoft is researching this behavior and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a Table (name it Test) with a general field (name it Pic).
	
	2. Embed a .bmp file into the general field Pic.
	
	3. Execute the program as follows:
	
	  
	
	        CLOSE data
	        SELECT 0
	        USE Test
	        DO while .t.
	        @ 1,1 SAY Pic
	        ENDDO
	
	The amount of time the loop runs varies depending on your processor, memory, and
	operating system.
	
	Additional query words: kbdse vFoxWin
	
	======================================================================
	Keywords          : kberrmsg kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600
	Version           : 3.00 3.00b 5.00
	
	=============================================================================
	

{% endraw %}
