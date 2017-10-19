---
layout: page
title: "Q158847: WD97: Run-Time Error '5841' If Style Doesn't Exist"
permalink: kb/158/Q158847/
---

## Q158847: WD97: Run-Time Error '5841' If Style Doesn't Exist

	Article: Q158847
	Product(s): Word 97 for Windows
	Version(s): 97
	Operating System(s): 
	Keyword(s): kberrmsg kbdta kbdtacode word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you run a Visual Basic for Applications macro that modifies or deletes a
	specific style, the following error message may appear:
	
	  Run-time error '5841': The requested member of the collection does not exist.
	
	CAUSE
	=====
	
	This problem occurs if you attempt to modify or delete a style that does not
	exist.
	
	WORKAROUND
	==========
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The following Microsoft Visual Basic for Applications example code tests for the
	presence of a specific style. If the style exists, the macro checks to see
	whether the specified style is a built-in style. If it is not a built-in style,
	the macro tests whether the style is currently in use. If the style is in use,
	the style is deleted.
	
	  Sub DoesStyleExist()
	     Dim styStyle As Style
	     Dim sMsg As String
	     Dim sStyleName As String
	     ' The style to delete.
	     ' Note: Character case is utilized with styles.
	     ' For example, "mystyle" is different from "MYSTYLE".
	     sStyleName = "mystyle"
	     ' Initial message.
	     sMsg = " style does not exist."
	     For Each styStyle In ActiveDocument.Styles
	        ' Does the style exist?
	        If styStyle.NameLocal = sStyleName Then
	           ' Cannot delete a built in style.
	           If styStyle.BuiltIn = False Then
	              ' Is the style being used?
	              If styStyle.InUse Then
	                 ' Delete the Style
	                 styStyle.Delete
	                 sMsg = " style has been deleted."
	                 Exit For
	              End If
	           Else
	              sMsg = " style is a built-in style."
	              Exit For
	           End If
	        End If
	     Next
	     ' Display a message indicating the resulting action.
	     MsgBox sStyleName & sMsg
	  End Sub
	
	For information about how to do this in earlier versions of Word, please see the
	following article in the Microsoft Knowledge Base:
	
	  
	
	  Q117826 WD: WordBasic Macro to Test for an Existing Style Name
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  
	
	  Q173707 FF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: wordcon vb vba vbe 5841 doesn t
	
	======================================================================
	Keywords          : kberrmsg kbdta kbdtacode word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : :97
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	