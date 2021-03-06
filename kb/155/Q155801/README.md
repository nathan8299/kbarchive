---
layout: page
title: "Q155801: WD97: CTRL+Page Up/Down Keys, Previous/Next Page Buttons Change"
permalink: /kb/155/Q155801/
---

## Q155801: WD97: CTRL+Page Up/Down Keys, Previous/Next Page Buttons Change

{% raw %}

	Article: Q155801
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbualink97 kbusage kbmacroexample kbwordvba word97kbfaq
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	In Microsoft Word 97, the color of the Previous Page and Next Page buttons on
	the vertical scroll bar change to blue, and the ToolTips change to Previous
	Find/GoTo and Next Find/GoTo.
	
	Also, when you press these buttons or their shortcut keys (CTRL+PAGE UP or
	CTRL+PAGE DOWN), the insertion point either remains in the same place, goes to
	an incorrect location, or Word displays the following message:
	
	  Word has reached the {beginning or end} of the document. Do you want to
	  continue searching at the {beginning or end}?
	
	
	CAUSE
	=====
	
	The Previous Page and Next Page buttons are black by default. When a different
	browse object type is selected, other than Browse By Page, the buttons turn blue
	to indicate that the Previous and Next buttons have been reassigned. The
	ToolTips for these buttons also indicate the current button assignments.
	
	For example, the prompt to "continue searching" indicates that a search is
	active, and the buttons have been reassigned to Previous Find/GoTo and Next
	Find/GoTo.
	
	WORKAROUND
	==========
	
	Use any of the following methods to reset the Previous and Next buttons to
	Previous Page and Next Page.
	
	Method 1: Reset the Select Browse Object to Browse By Page
	----------------------------------------------------------
	
	Click the Select Browse Object button (located between the Next and Previous
	buttons on the scroll bar), and then click the Browse By Page icon (far right,
	top row).
	
	Method 2: Create Macros to Reset the Buttons Automatically
	----------------------------------------------------------
	
	Microsoft provides examples of Visual Basic for Applications procedures for
	illustration only, without warranty either expressed or implied, including, but
	not limited to the implied warranties of merchantability and/or fitness for a
	particular purpose. The Visual Basic procedures in this article are provided 'as
	is' and Microsoft does not guarantee that they can be used in all situations.
	While Microsoft support professionals can help explain the functionality of a
	particular macro, they will not modify these examples to provide added
	functionality, nor will they help you construct macros to meet your specific
	needs. If you have limited programming experience, you may want to consult one
	of the Microsoft Solution Providers. Solution Providers offer a wide range of
	fee-based services, including creating custom macros. For more information about
	Microsoft Solution Providers, call Microsoft Customer Information Service at
	(800) 426-9400.
	
	You will need to create two macros (BrowseNext and BrowsePrev) that will
	automatically reset the Browse Object buttons when you click them. Use the
	following procedure to create the macros.
	
	To create the BrowseNext macro, follow these steps:
	
	1. Create a new Word 97 document.
	
	2. On the Tools menu, point to Macro, and then click Macros.
	
	3. Under Macro Name, type "BrowseNext" (without the quotation marks). In the
	  Macros In box, click to select "All active templates and Documents," and then
	  click Create.
	
	  NOTE: This macro has to be called BrowseNext so that it will function When you
	  click the Next Page button.
	
	4. Change the existing BrowseNext macro to the following:
	
	        Sub BrowseNext()
	        '
	        ' BrowseNext Macro
	        ' Jump to the next browse object.
	        '
	           Application.Browser.Target=wdBrowsePage
	           Application.Browser.Next
	
	        End Sub
	
	5. On the File menu, click Save Normal.
	
	6. On the File menu, click Close and Return to Microsoft Word.
	
	To create the BrowsePrev macro, follow these steps:
	
	1. With your new Word 97 document still open, on the Tools menu, point to Macro,
	  and then click Macros.
	
	2. Under Macro Name type "BrowsePrev" (without the quotation marks). In the
	  Macros In box, click to select "All active templates and documents", and then
	  click Create.
	
	  NOTE: This macro has to be called BrowsePrev so that it will function when you
	  click the Previous Page button.
	
	3. Change the existing BrowsePrev macro to the following:
	
	        Sub BrowsePrev()
	        '
	        ' BrowsePrev Macro
	        ' Jump to the previous browse object
	        '
	           Application.Browser.Target=wdBrowsePage
	           Application.Browser.Previous
	        End Sub
	
	4. On the File menu, click Save Normal.
	
	5. On the File menu, click "Close and Return to Microsoft Word."
	
	Method 3: Record Resetting the Select Browse Object to Browse by Page
	---------------------------------------------------------------------
	
	To record the action of resetting the Browse Object to Browse by Page:
	
	1. On the Tools menu, point to Macro, and click Record New Macro.
	
	2. Enter a name for the macro in the Macro Name box, and click OK.
	
	3. Click the Select Browse Object button (located between the Next and Previous
	  buttons on the scroll bar), and then click the Browse By Page icon (far
	  right, top row).
	
	4. On the Tools menu, point to Macro, and click Stop Recording.
	
	You can then assign this macro to a toolbar or menu item.
	
	For more information about how to assign a macro to a toolbar, click the Office
	Assistant, type "How do I assign a macro" (without the quotation marks), click
	Search, click the "Add a button to a toolbar" topic, and then click to view "Add
	a button to a toolbar."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Microsoft Help is not installed on your computer, please
	see the following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	MORE INFORMATION
	================
	
	Browse Buttons
	--------------
	
	The Select Browse Object button (located between the Next and Previous buttons on
	the scrollbar) enables you to select a number of additional object types. Word
	may assign one of the following properties to the Next and Previous buttons
	after you attempt to go to any of these objects:
	
	  Field
	  Endnote
	  Footnote
	  Comment
	  Section
	  Edits
	  Heading
	  Graphic
	  Table
	
	For example, if you attempt to go to a comment, the buttons change to Previous
	Comment and Next Comment. Another example would be when you click Find on the
	Edit menu. Once you click Find to find an item, the Select Browse Object buttons
	will be set to Next or Previous Find/GoTo.
	
	For more information about the Select Browse Object buttons, click the Office
	Assistant, type "What is select browse object?" (without the quotation marks),
	click Search, click the "Move around in a document" topic, and then click to
	view "Scroll through a document by using the mouse."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Microsoft Help is not installed on your computer, please
	see the following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	CTRL+PAGE UP and CTRL+PAGE DOWN
	-------------------------------
	
	When you press the CTRL+PAGE DOWN shortcut key, Word should place the insertion
	point at the top of the next page.
	
	When you press the CTRL+PAGE UP shortcut key, Word should place the insertion
	point at the top of the previous page.
	
	Additional query words: 8.0 8.00 replace pageup pagedown pgup pgdn
	
	======================================================================
	Keywords          : kbualink97 kbusage kbmacroexample kbwordvba word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
