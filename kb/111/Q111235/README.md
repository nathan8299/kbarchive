---
layout: page
title: "Q111235: BUG: D2030 or DX1020 Error on Assumed-Size Array Expressions"
permalink: /kb/111/Q111235/
---

## Q111235: BUG: D2030 or DX1020 Error on Assumed-Size Array Expressions

{% raw %}

	Article: Q111235
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0,1.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FORTRAN PowerStation for MS-DOS, versions 1.0, 1.0a 
	- Microsoft Fortran Powerstation 32 for Windows NT, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Compiling a file that contains an assumed-size array expression may produce the
	following error under Windows NT:
	
	  Command Line Error D2030: INTERNAL COMPILER ERROR
	
	Under straight MS-DOS, the following error may be produced during compilation:
	
	  DOSXNT : fatal error DX1020: unhandled exception: Page fault;
	
	Under the Windows MS-DOS box, no error is produced. The appropriate errors for
	this situation are:
	
	  error F2652: array expression: cannot be assumed-size array
	
	  error F2564: incompatible types in assignment
	
	CAUSE
	=====
	
	Because the size of an assumed-sized array is not known at compile time, you
	cannot use an assumed-size array in an array expression.
	
	RESOLUTION
	==========
	
	Do not use assumed-size arrays in array expressions.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in FORTRAN PowerStation 32 for
	Windows NT version 1.0 and MS-DOS version 1.0 and 1.0a. We are researching this
	problem and will post new information here in the Microsoft Knowledge Base as it
	becomes available.
	
	MORE INFORMATION
	================
	
	The following sample illustrates the problem:
	
	Sample Code
	-----------
	
	  c Compile options needed: none
	  c
	        INTEGER*2 FUNCTION GETSP(SPVALU)
	        INTEGER*2       COMBUF
	        INTEGER*2       SPVALU(*)
	        SPVALU = COMBUF  !  Array expression sets each element to COMBUF
	        END
	
	Additional query words: 1.00 1.00a ICE array operations
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFortranSearch kbZNotKeyword2 kbZNotKeyword3 kbFORTRANPower32100NT kbFORTRANPower100DOS kbFORTRANPower100aDOS
	Version           : :1.0,1.0a
	
	=============================================================================
	

{% endraw %}
