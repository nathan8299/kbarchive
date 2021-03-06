---
layout: page
title: "Q161497: FIX: SYS(2014) Function Returns Incorrect Path"
permalink: /kb/161/Q161497/
---

## Q161497: FIX: SYS(2014) Function Returns Incorrect Path

{% raw %}

	Article: Q161497
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b,5.0
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300bBUG kbvfp500aFIX kbvfp500bugkbbuglist kbfixlist
	Last Modified: 04-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a file name consists of periods along with the file extension, the SYS(2014)
	function does not return the correct path. According to the SYS(2014) Help
	topic, the SYS(2014) function "returns the minimum path relative to the current
	or specified directory or folder for a specified file."
	
	Note: The word "folder" appears in the Visual FoxPro 3.0 Help file but not in the
	Visual FoxPro 5.0 Help file.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been fixed in Visual FoxPro
	5.0a.
	
	MORE INFORMATION
	================
	
	The SYS(2014) function returns different values depending on the version of
	Visual FoxPro currently running.
	
	Steps to Reproduce Behavior
	---------------------------
	
	- In Visual FoxPro 3.0b, issue the following commands in the Command window:
	
	  " ?SYS(2014,"Samples\Data\........dbf")
	  ?SYS(2014,"Samples\Data\employee.dbf") " (without the quotation marks)
	
	  The following paths appear on the desktop:
	
	  SAMPLES......DBF
	  SAMPLES\DATA\EMPLOYEE.DBF
	
	-or-
	
	- In Visual FoxPro 5.0, issue the following commands in the Command window:
	
	  " ?SYS(2014,"Samples\Data\........dbf")
	  ?SYS(2014,"Samples\Data\employee.dbf") " (without the quotation marks)
	
	  The following paths appears on the desktop:
	
	  " .....DBF
	  \VFP5\SAMPLES\DATA\EMPLOYEE.DBF " (without the quotation marks)
	
	The SYS(2014) function should actually report the following value for the path
	when a file name consists of period characters:
	
	  \SAMPLES\DATA\........DBF
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp300bBUG kbvfp500aFIX kbvfp500bug kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500
	Version           : WINDOWS:3.0,3.0b,5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
