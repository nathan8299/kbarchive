---
layout: page
title: "Q119900: INFO: Understanding the RETURN Command"
permalink: /kb/119/Q119900/
---

## Q119900: INFO: Understanding the RETURN Command

{% raw %}

	Article: Q119900
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5x; MS-DOS:2.0,2.5x,2.6,2.6a; UNIX:2.6; WINDOWS:2.5x,2.6,2.6a,3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 30-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5x, 2.6, 2.6a 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, version 2.5x 
	- Microsoft FoxPro for UNIX, version 2.6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The RETURN command provides a great deal of flexibility over program control.
	RETURN terminates execution of a program, procedure, or function. Depending on
	how RETURN is used, control is returned to the calling program, the
	highest-level calling program, another program, or the Command window. The
	sample code below illustrates the power of the RETURN command.
	
	MORE INFORMATION
	================
	
	Enter the following code in a program call RETTEST.PRG:
	
	
	  PARAMETER x  && line 1
	
	  ON ERROR DO myErr
	  DO A
	  WAIT WINDOW 'In master'   && line 5
	
	  ON ERROR
	
	  PROCEDURE A
	  DO B
	  WAIT WINDOW 'In A'   && line 11
	
	  PROCEDURE B
	  x=testing
	  WAIT WINDOW 'In B'  && line 15
	
	  PROCEDURE myErr
	  DO CASE
	
	  CASE x = 'master' RETURN TO MASTER CASE EMPTY(x) RETURN OTHERWISE RETURN TO
	  &x
	
	  ENDCASE
	
	
	To demonstrate the capabilities of the RETURN command, try the following three
	invocations of the above program from the Command window.
	
	- The following command returns to line 5 without executing lines 11 or 15: DO
	  rettest WITH "master"
	
	- The following command returns to line 11 without executing line 15: DO
	  rettest WITH "A"
	
	- The following command returns to line 15, the line of code immediately
	  following the line that generated the error: DO rettest WITH ""
	
	The program is so short that it may be helpful to use the Trace window and step
	through the code. For additional information about using the Trace window, see
	the "Debugging" chapter of the "Developer's Guide" and the "Program Menu"
	chapter of the "User's Guide."
	
	REFERENCES
	==========
	
	FoxPro "Language Reference"
	
	Additional query words: VFoxWin FoxUnix FoxMac FoxDos FoxWin 2.50 2.50a 2.50b 2.50c
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260UNIX kbFoxPro260 kbFoxPro260a kbVFP300 kbVFP500 kbVFP600
	Version           : MACINTOSH:2.5x; MS-DOS:2.0,2.5x,2.6,2.6a; UNIX:2.6; WINDOWS:2.5x,2.6,2.6a,3.0,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
