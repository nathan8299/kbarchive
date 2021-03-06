---
layout: page
title: "Q139188: FIX: Cannot Click a List Box on a Pageframe by Using the Mouse"
permalink: /kb/139/Q139188/
---

## Q139188: FIX: Cannot Click a List Box on a Pageframe by Using the Mouse

{% raw %}

	Article: Q139188
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300bBUG kbvfp500fixkbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a form contains a pageframe that has at least two pages and each page
	contains a list box, a mouse click in the list box on the first page may have no
	effect.
	
	CAUSE
	=====
	
	The Visible property of the list box on the second page has been modified but is
	still set to the default of true.
	
	WORKAROUND
	==========
	
	Modify the Visible property of the second list box to reset it to the default by
	right-clicking the Visible property and then clicking Reset to Default.
	
	Resetting the default value of properties may correct other unexpected behavior
	of a form or its objects. For more information about this problem, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q143400 PRB: Resetting Defaults May Fix Form Misbehavior in VFP
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem has been fixed in Visual FoxPro 5.0
	for Windows.
	
	MORE INFORMATION
	================
	
	This problem occurs only if the list box on the first page is positioned at the
	same location as the list box on the second page. It also occurs in a pageframe
	that has more than two pages. The problem occurs even if the list boxes are not
	on consecutive pages as long as they are positioned on their respective pages in
	the same location.
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Create a new form, and place a PageFrame object on the form.
	
	2. On the first page of the PageFrame, place a list box.
	
	3. Size the list box to cover the entire page.
	
	4. Set the RowSourceType property of the list box to 1 - Value.
	
	5. Set the RowSource property of the list box to 1,2,3,4.
	
	6. Copy the list box from page one to page two of the pageframe.
	
	7. Modify the Visible property of the list box on page two by selecting the
	  property in the property window and pressing ENTER. This should change the
	  Visible property text in the property window from a normal font to a bold
	  font. Notice that the property is still set to true, which is the default.
	
	8. Save and run the form.
	
	You will notice that a mouse click in the first list box will not have any
	effect. If at this point you select the second page and then change back to the
	first page, you should be able to click the first list box.
	
	The problem of erratic appearance and behavior can occur in other instances as
	well where the default value appears bolded. Rightmouse clicking and resetting
	to default from the menu corrects the problem.
	
	Additional query words: listbox pageframe
	
	======================================================================
	Keywords          : kbvfp kbvfp300bBUG kbvfp500fix kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b
	Version           : WINDOWS:3.0,3.0b
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
