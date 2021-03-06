---
layout: page
title: "Q159907: PRB: Missing Window Buttons if Form ControlBox Property False"
permalink: /kb/159/Q159907/
---

## Q159907: PRB: Missing Window Buttons if Form ControlBox Property False

{% raw %}

	Article: Q159907
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbnokeyword kbVBp kbVBp400 kbVBp500 kbVBp600 kbOSWin98 kbGrpDSVB kbDSupport kbOSWinME
	Last Modified: 26-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When 32-bit Visual Basic applications run on Windows 95, Windows 98, Windows Me,
	Windows NT 4.0, and Windows 2000, the three Window buttons in the upper-right
	corner of a form (Minimize, Maximize, and Close) disappear if the ControlBox
	property of that form is set to False. In 16-bit Visual Basic applications, the
	Close Window button is disabled and the Minimize and Maximize Window buttons
	remain visible and enabled. The difference between 32-bit and 16- bit Visual
	Basic applications is not observed on Windows NT 3.51 because it has a different
	user interface.
	
	CAUSE
	=====
	
	The difference described above is by design. The user-interface specifications
	for Windows 95, Windows 98, Windows Me, Windows NT 4.0, and Windows 2000 enforce
	different UI behaviors for 32-bit applications versus 16-bit applications.
	
	RESOLUTION
	==========
	
	To keep the Minimize and Maximize buttons visible and enabled while disabling
	the Close button, follow these steps:
	
	1. Start 32-bit Visual Basic. Form1 is created by default.
	
	2. Type the following code in the General Declarations section.
	
	     Option Explicit
	     Private Declare Function GetSystemMenu Lib "user32" (ByVal hwnd As Long,
	     ByVal bRevert As Long) As Long
	     Private Declare Function DeleteMenu Lib "user32" (ByVal hMenu As Long,
	     ByVal nPosition As Long, ByVal wFlags As Long) As Long
	     Private Declare Function SendMessage Lib "user32" Alias "SendMessageA"
	     (ByVal hwnd As Long, ByVal wMsg As Long, ByVal wParam As Long, lParam As
	     Long) As Long
	     Private Const SC_CLOSE = &HF060
	     Private Const SC_MOVE = &HF010
	     Private Const SC_SIZE = &HF000
	     Private Const MF_BYCOMMAND = &H0&
	     Private Const WM_NCACTIVATE = &H86
	
	3. Type the following code in the Form_Load event procedure:
	
	     Private Sub Form_Load()
	         Dim hMenu As Long, Success As Long
	
	         hMenu = GetSystemMenu(Form1.hwnd, 0)
	         Success = DeleteMenu(hMenu, SC_SIZE, MF_BYCOMMAND)
	         Success = DeleteMenu(hMenu, SC_MOVE, MF_BYCOMMAND)
	         Success = DeleteMenu(hMenu, SC_CLOSE, MF_BYCOMMAND)
	         SendMessage Form1.hwnd, WM_NCACTIVATE, 0&, 0&
	         SendMessage Form1.hwnd, WM_NCACTIVATE, 1&, 0&
	     End Sub
	
	4. Run the program. The Close button on the upper-right corner of Form1 is
	  disabled while the Minimize and Maximize buttons remain visible and enabled.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnokeyword kbVBp kbVBp400 kbVBp500 kbVBp600 kbOSWin98 kbGrpDSVB kbDSupport kbOSWinME 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : :4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
