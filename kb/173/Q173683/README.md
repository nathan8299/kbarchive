---
layout: page
title: "Q173683: WD97: Error Message: &quot;Word Cannot Give a Document the Same Name&quot;"
permalink: /kb/173/Q173683/
---

## Q173683: WD97: Error Message: &quot;Word Cannot Give a Document the Same Name&quot;

{% raw %}

	Article: Q173683
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word8 word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Word 97, you may receive the following error message:
	
	  Word cannot give a document the same name as an open document.
	
	  Type a different name for the document you want to save.
	  (<path>\filename)
	
	When you click OK, Word displays the Save As dialog box, prompting you to save
	the document.
	
	This error may occur with large documents if you select the following options on
	the Save tab (click Options on the Tools menu):
	
	- Allow Fast Saves
	
	  -and-
	
	- Allow Background Saves
	
	  -and-
	
	- Save AutoRecover info every <n> minutes
	
	CAUSE
	=====
	
	This error may occur when you attempt to save a document, while Word is
	performing an automatic background save. Both save processes are trying to save
	information to the same file name.
	
	WORKAROUND
	==========
	
	To prevent this error message from occurring, allow the automatic background
	save to complete before you save your document.
	
	NOTE: When Word saves a document in the background, a pulsing disk icon appears
	on the status bar.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.<A0>This problem was corrected in Microsoft
	Word 2000.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q89247 WD97: How Word for Windows Uses Temporary Files
	
	  Q71999 WD97: How to Disable the Fast Saves Option
	
	  Q107686 WD: How Word Creates and Recovers AutoRecover Files
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbdta word8 word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
