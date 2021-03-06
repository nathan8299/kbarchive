---
layout: page
title: "Q318993: FIX: XMLToCursor() Truncates Data on DBCS System"
permalink: /kb/318/Q318993/
---

## Q318993: FIX: XMLToCursor() Truncates Data on DBCS System

{% raw %}

	Article: Q318993
	Product(s): Microsoft FoxPro
	Version(s): 7.0
	Operating System(s): 
	Keyword(s): kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283
	Last Modified: 14-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you run Visual FoxPro 7.0 on a Double-byte Character Set (DBCS) enabled
	system, the XMLToCursor() function truncates data. The resulting field is only
	half as long as it should be, and the last half of the data is truncated.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Visual FoxPro for
	Windows 7.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q316964 How to Obtain the Latest Visual FoxPro for Windows 7.0 Service Pack
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Visual FoxPro for
	Windows 7.0. This problem was first corrected in Visual FoxPro for Windows 7.0
	Service Pack 1.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce the Problem
	------------------------------
	
	Run the following code from Visual FoxPro 7.0 on a DBCS-enabled system (such as
	Chinese Microsoft Windows 2000):
	
	  LOCAL lccCharsDB AS STRING
	
	  CLEAR
	  CLOSE DATABASES ALL
	  CD JUSTPATH(SYS(16))
	  lcCharsDB = CHR(191) + CHR(201) + ;
	  	CHR(209) + CHR(211) + ;
	  	CHR(201) + CHR(236) + ;
	  	CHR(152) + CHR(203) + ;
	  	CHR(202) + CHR(190) + ;
	  	CHR(213) + CHR(90) + ;
	  	CHR(209) + CHR(212)
	  CREATE TABLE DBCS (memo1 m)
	  INSERT INTO DBCS VALUES (lcCharsDB)
	  CURSORTOXML("DBCS", "MyString.xml", 1, 512)
	  TYPE MyString.XML
	  XMLTOCURSOR("MyString.xml", "MyCursor", 512)
	  SELECT mycursor
	  BROWSE
	
	  *~ Clean Up
	  USE IN MyCursor
	  USE IN DBCS
	  ERASE MyString.XML
	  ERASE DBCS.DBF
	  ERASE DBCS.FPT
	
	Notice that when you browse the table, the memo1 field is only half as long as it
	should be. The remaining data is truncated.
	
	Additional query words: kbVFP700sp1fix
	
	======================================================================
	Keywords          : kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP700
	Version           : :7.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
