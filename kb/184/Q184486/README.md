---
layout: page
title: "Q184486: WD97: Personal Info Style Applied as Style of Next Paragraph"
permalink: /kb/184/Q184486/
---

## Q184486: WD97: Personal Info Style Applied as Style of Next Paragraph

{% raw %}

	Article: Q184486
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you type information in a paragraph using the Personal Info style (in the
	Contemporary Resume template) and press ENTER to start a new paragraph, the
	space between the paragraphs is larger than you expected.
	
	CAUSE
	=====
	
	In the Personal Info style definition, the style definition for the following
	paragraph is set to Personal Info rather than to Achievement.
	
	WORKAROUND
	==========
	
	To work around this behavior, after you press ENTER to start a new paragraph,
	apply the Achievement style to the new paragraph. To do this, use one of the
	following methods.
	
	Method 1: Use the Style list on the Formatting toolbar
	------------------------------------------------------
	
	After you press ENTER, change the style of the new paragraph by click the Style
	list on the Formatting toolbar and then clicking Achievement.
	
	Method 2: Use the Style command on the Format menu
	--------------------------------------------------
	
	1. On the Format menu, click Style.
	
	2. Under Styles, click Achievement.
	
	3. Click Apply.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	To determine how a style is defined, including what style is being used by the
	following paragraph, follow these steps:
	
	1. On the Format menu, click Style.
	
	2. From the Styles list, select the style of the current paragraph.
	
	3. Click Modify.
	
	4. Under Style For Following Paragraph, you will see the style that will be
	  applied to the next paragraph when you press ENTER.
	
	Additional query words: word97 word8
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
