---
layout: page
title: "Q175443: FIX: Application Error When Binding Dynamically-Created Control"
permalink: /kb/175/Q175443/
---

## Q175443: FIX: Application Error When Binding Dynamically-Created Control

{% raw %}

	Article: Q175443
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbVBp kbVBp400bug kbVBp500fix kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An application error occurs when a Visual Basic program dynamically creates a
	text box bound to a remote data control or a data control.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been corrected in Visual Basic, version
	5.0.
	
	MORE INFORMATION
	================
	
	This section shows you how to reproduce the bug in Visual Basic 4.0 using a data
	control. You can substitute a remote data control for a data control and still
	reproduce the behavior.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start 32-bit Visual Basic 4.0 or, if it is already running, click New Project
	  on the File menu.
	
	2. Add the following controls to Form1 and set the following properties to the
	  appropriate controls:
	
	  Control           Default Name     Property            Setting
	  ---------------------------------------------------------------
	  Command Button    Command1
	
	  Data              Data1            DatabaseName        Biblio.mdb
	                                     RecordSource        Authors
	
	  Text Box          Text1            DataSource          Data1
	                                     Index               0
	
	3. Copy the following code to the Code window of Form1:
	
	        Option Explicit
	
	        Private Sub Form_Load()
	           Command1.Caption = "For Remote Data Control"
	        End Sub
	
	        Private Sub Command1_Click()
	           Dim count As Integer
	           Dim i As Integer
	           Static lastcount As Integer
	
	           Data1.Refresh
	           count = 4
	
	           If lastcount > 0 Then
	              For i = lastcount - 1 To 1 Step -1
	                 Unload text1(i)
	              Next i
	           End If
	
	           If count > 0 Then
	              For i = 1 To count - 1
	                 Load text1(i)
	                 text1(i).Left = text1(0).Left + (i * 1335)
	                 text1(i).Visible = True
	              Next i
	           End If
	           lastcount = count
	        End Sub
	
	4. On the Run menu, click Start or press the F5 key to start the program. Each
	  time you click the command button, three text boxes appear. On the third
	  click, an application error occurs displaying one of the following messages
	  and Visual Basic ends:
	
	
	  Windows NT 3.51:
	
	  An application error has occurred and an application error log is
	  being generated.VB32.exe.
	  Exception: access violation (0xc0000005), Address: 0x00402a38
	
	  Windows 95:
	
	  VB32 caused an invalid page fault in module VB32.EXE at 0137:00402a3a.
	
	  -and-
	
	  VB32 caused an invalid page fault in module KERNEL32.DLL at 0137:bff9a07c.
	
	  Windows 98:
	
	  VB32 caused an invalid page fault in module VB32.EXE at 015f:00402a3a.
	
	  -or-
	
	  VB32 caused an invalid page fault in module KERNEL32.DLL at 015f:bff9d706.
	
	Additional query words: ipf gpf crash kbTextBox
	
	======================================================================
	Keywords          : kbVBp kbVBp400bug kbVBp500fix kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Version           : WINDOWS:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
