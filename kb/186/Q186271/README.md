---
layout: page
title: "Q186271: HOWTO: Manipulate Text Box Contents"
permalink: /kb/186/Q186271/
---

## Q186271: HOWTO: Manipulate Text Box Contents

{% raw %}

	Article: Q186271
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article illustrates how to manipulate the contents of a text box by using a
	combination of text box properties and calling functions from the Windows API.
	You can use the techniques in this article to extend the features of a text box.
	The article also shows you how to create a sample project that demonstrates how
	to manipulate the contents of a text box.
	
	MORE INFORMATION
	================
	
	This article assumes you are familiar with using the functions in the Windows
	API. The article will show you how to do the following:
	
	- Determine the cursor position in a text box.
	
	- Determine the line number of the line where your cursor is positioned in a
	  multi-line text box.
	
	- Determine the length of a selected line.
	
	- Show all the text of a selected line.
	
	- Insert text at a cursor position.
	
	The first task uses a text box property. The remaining tasks use the SendMessage
	API function with the handle of the text box, a message, and the parameters
	required for that message.
	
	To determine the cursor position in a text box, use the SelStart property of the
	text box. This property returns the position of the text relative to the first
	character of the first line. If you select a block of text, you can determine
	the cursor position by adding the SelLength property to the SelStart property.
	
	The other three tasks require the SendMessage function with the Hwnd property of
	the text box, the appropriate message, and the required message parameters. The
	declaration of the SendMessage function is as follows:
	
	     Private Declare Function SendMessage Lib "user32" Alias "SendMessageA" _
	        (ByVal hwnd As Long, ByVal wMsg As Long, ByVal wParam As Long, _
	        ByVal lParam As String) As Long
	
	The following messages are used:
	
	- EM_LINEFROMCHAR (&HC9)-returns the line number of the line where the
	  cursor is positioned. Pass the cursor position with this message.
	
	- EM_LINELENGTH (&HC1)-returns the length of the line where the cursor is
	  positioned. Pass the cursor position with this message.
	
	- EM_LINEINDEX (&HBB)-returns the number of characters in all the lines
	  previous to the cursor position. Pass the results of the EM_LINEFROMCHAR
	  message. Each line includes a carriage return and a line feed character.
	
	- EM_GETLINECOUNT (&HBA)-returns the total number of lines in a multi-line
	  text box.
	
	- EM_GETLINE (&HC4)-returns the text of the line where the cursor is
	  positioned. Pass the results of the EM_LINEFROMCHAR message.
	
	The next section shows how to create a sample project that demonstrates how to
	manipulate text in a text box.
	
	Steps to Create Sample Project
	------------------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Add a CommandButton, two Label controls and two Text boxes to Form1 and set
	  the following properties to the appropriate controls:
	
	  Control           Default Name     Property            Setting
	  ---------------------------------------------------------------
	  Text Box          Text1            MultiLine           True
	
	  Label             Label1           AutoSize            True
	
	3. Copy the following code to the Code window of the Form1 form:
	
	        Option Explicit
	
	        Private Declare Function SendMessage Lib "user32" _
	                                               Alias "SendMessageA" _
	                                               (ByVal hwnd As Long, _
	                                               ByVal wMsg As Long, _
	                                               ByVal wParam As Long, _
	                                               ByVal lParam As String) _
	                                               As Long
	
	        Private Const EM_GETLINE = &HC4
	        Private Const EM_GETLINECOUNT = &HBA
	        Private Const EM_LINEFROMCHAR = &HC9
	        Private Const EM_LINEINDEX = &HBB
	        Private Const EM_LINELENGTH = &HC1
	        Private Const EM_REPLACESEL = &HC2
	
	        Private Sub Form_Load()
	           With Command1
	              .Caption = "Insert This Text"
	              .Height = 375
	              .Left = 120
	              .Top = 3000
	              .Width = 1455
	           End With
	
	           With Form1
	              .Caption = "Enhanced Text Box Sample Project"
	              .Height = 4485
	              .Width = 6990
	           End With
	
	           With Label1
	              .Height = 195
	              .Left = 120
	              .Top = 240
	              .Width = 3015
	              .WordWrap = True
	           End With
	
	           With Label2
	              .Height = 255
	              .Left = 1800
	              .Top = 3360
	              .Width = 3135
	           End With
	
	           With Text1
	              .Height = 2655
	              .Left = 3360
	              .Top = 240
	              .Width = 3375
	           End With
	
	           With Text2
	              .Height = 285
	              .Left = 1680
	              .Top = 3000
	              .Width = 5055
	           End With
	
	        End Sub
	
	        Private Sub Command1_Click()
	           Call SendMessage(Text1.hwnd, EM_REPLACESEL, 0, Text2.Text)
	           Label2.Caption = "Copied text is " + Text2.Text
	           ShowInfo
	        End Sub
	
	        Private Sub Text1_KeyUp(KeyCode As Integer, Shift As Integer)
	           ShowInfo
	        End Sub
	
	        Private Sub Text1_MouseMove(Button As Integer, _
	                                      Shift As Integer, _
	                                      X As Single, _
	                                      Y As Single)
	           ShowInfo
	        End Sub
	
	        Private Function ShowInfo()
	        '********************************************************************
	        ' Purpose:  Runs all the functions to get the necessary information
	        '           in order to create the information text string. The text
	        '           string is then displayed in the label control.
	        '********************************************************************
	
	           Dim strInfo As String
	           Dim lCurPos As Long
	           Dim lCurLineNum As Long, lTotLines As Long, lLineLength
	           Dim lNumBChar As Long
	           Dim sCurLine As String * 25
	
	           'Determine Cursor Position
	           If Text1.SelLength = 0 Then
	              lCurPos = Text1.SelStart
	           Else
	              lCurPos = Text1.SelStart + Text1.SelLength
	           End If
	
	           'Determine Line Number
	           lCurLineNum = SendMessage(Text1.hwnd, EM_LINEFROMCHAR, lCurPos, 0)
	
	           'Determine the Line Length
	           lLineLength = SendMessage(Text1.hwnd, EM_LINELENGTH, lCurPos, 0)
	
	           'Determine the number of characters in lines before current
	           'cursor position. Note that the number of characters includes a
	           'carriage return and line feed characters at the end of each
	           'line.
	           lNumBChar = SendMessage(Text1.hwnd, EM_LINEINDEX, lCurLineNum, 0)
	
	           'Determine Total number of lines
	           lTotLines = SendMessage(Text1.hwnd, EM_GETLINECOUNT, 0, 0)
	
	           'Determine Current Line
	           sCurLine = Space(25)
	           Call SendMessage(Text1.hwnd, EM_GETLINE, lCurLineNum, sCurLine)
	
	           'Display the information
	           strInfo = "Current Line: " + sCurLine + vbLf + _
	                     "Line Length: " + CStr(lLineLength) + _
	                     " Characters" + vbLf + _
	                     "Line Number: " + CStr(lCurLineNum + 1) + _
	                     " of " + CStr(lTotLines) + " Total Lines" + vbLf + _
	                     "Cursor Position: " + CStr(lCurPos) + vbLf + _
	                     "Total Characters in Previous Lines: " + _
	                     CStr(lNumBChar) + vbLf + _
	                     "Selected Length: " + CStr(Text1.SelLength) + vbLf + _
	                     "Selected Text: " + Text1.SelText
	
	           Label1.Caption = strInfo
	
	        End Function
	
	4. On the Run menu, click Start or press the F5 key to start the program. Click
	  inside the Text1 text box to display the text box information in Label1. To
	  insert text into the Text1 text box, position the cursor in the Text1 text
	  box where you want the text to be inserted. Enter the insertion text in the
	  Text2 text box and click the CommandButton.
	
	(c) Microsoft Corporation 1998, All Rights Reserved.
	Contributions by Fred Nava, Microsoft Corporation
	
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Arsenio
	Locsin, Microsoft Corporation
	
	
	Additional query words: kbDSupport kbDSD kbSDKWin32 kbAPI kbVBp500 kbVBp600 kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
