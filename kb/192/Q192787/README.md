---
layout: page
title: "Q192787: FIX: Modal Characteristics Gone After Selecting OS's Taskbar"
permalink: /kb/192/Q192787/
---

## Q192787: FIX: Modal Characteristics Gone After Selecting OS's Taskbar

{% raw %}

	Article: Q192787
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Clicking on the operating system's taskbar for any reason after running a modal
	form from another form allows the focus to return to the first form. Because the
	second form is modal, focus should not return to the first form. The forms must
	have the Desktop property set to True before this will occur.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been corrected in Visual FoxPro 6.0.
	
	MORE INFORMATION
	================
	
	Clicking on the Start button of the operating system's taskbar and starting
	another program would be the most common reason for leaving the FoxPro screen
	and then returning to find that focus can be set to the first form. After the
	first form receives focus, no object in the form can be accessed. Clicking on
	the second form will reactivate its modal characteristics.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create two forms, the first called Myform1 and the second called Myform2.
	
	2. Add a CommandButton to Myform1 and place the code DO FORM Myform2 in the
	  Click event.
	
	3. Change the Desktop property of both forms to True.
	
	4. Change the WindowType property to 1 - Modal in Myform2, and change the
	  AutoCenter property to True for convenience.
	
	5. Run the Myform1 and click on the CommandButton. After Myform2 comes up, click
	  on the operating system's taskbar, and then click back to Myform1, which will
	  receive focus, but you cannot select any objects. Only after clicking on
	  Myform2 will Myform2's modal characteristics take effect again.
	
	Additional query words: kbDSupport kbDse kbVFp600fix kbVFp500abug kbCtrl kbContainer
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : WINDOWS:5.0,5.0a
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
