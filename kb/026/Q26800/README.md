---
layout: page
title: "Q26800: FIX: No Error Generated by MASM 5.0 for Equates Made Public"
permalink: /kb/026/Q26800/
---

## Q26800: FIX: No Error Generated by MASM 5.0 for Equates Made Public

{% raw %}

	Article: Q26800
	Product(s): Microsoft Macro Assembler
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Macro Assembler version 5.0 will allow an equate to be made
	public.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM version 5.00. This problem
	was corrected in MASM version 5.10.
	
	MORE INFORMATION
	================
	
	The error generated by MASM 5.1 for the sample code below is:
	
	  A2014: Illegal public declaration
	
	MASM 5.0 incorrectly generates no errors.
	
	Sample Code:
	------------
	
	  ;Assemble options: none
	
	  PUBLIC i
	  i      equ <text>
	
	  end
	
	Additional query words: 5.00 buglist5.00 fixlist5.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM500
	Version           : :5.0
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
