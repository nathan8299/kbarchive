---
layout: page
title: "Q136997: How to Run a Code Resource from a Visual C++ Application"
permalink: /kb/136/Q136997/
---

## Q136997: How to Run a Code Resource from a Visual C++ Application

{% raw %}

	Article: Q136997
	Product(s): Microsoft C Compiler
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, Macintosh Cross-Development Addon, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article illustrates loading and executing stand-alone Code Resources from a
	Visual C++ application using the sample code shipped with the Visual C++
	Macintosh add-on.
	
	Chapter 8 of the 68K Programmer's Guide in the Visual C++ Books Online discusses
	using stand-alone code and shared libraries in 68K programs. This chapter
	provides a brief set of instructions on how to call a code resource. For more
	information on Macintosh Code Resources, please refer to this chapter in the
	Books Online.
	
	MORE INFORMATION
	================
	
	To load a Code Resource, the Macintosh System provides a function (GetResource)
	that will load any resources including code resources and return a handle to a
	code resource. Visual C++ provides a function (_PvApplyFixup) that will take a
	handle to a code resource and return a pointer to the entry point. You can use
	these two functions to run a code resource from a Visual C++ application. The
	following example demonstrates how to load and execute the SACODE sample's INIT
	code resource.
	
	Step-by-Step Example
	--------------------
	
	1. Build the SACODE sample project located in Msvc20\Samples\M68k\Sacode and
	  copy the resulting file to the Macintosh. Give the remote executable path and
	  file name. For example:
	
	  Macintosh HD:Testing:SACODE
	
	2. Make a copy of the SKEL sample located in Msvc20\Samples\M68k\Skel and call
	  it MYSKEL. Then, make the following modifications:
	
	  1. Add an include for Resource.h in Skel.c. For example, after this line:
	
	           #include <macos\QuickDra.h>
	
	        add this line:
	
	           #include <macos\Resource.h>
	
	  2. Add a prototype for _PvApplyFixup and modify the DoAbout function to look
	     like this:
	
	        extern ProcPtr _PvApplyFixup(Handle);
	
	        DoAbout ()
	        {
	        //   SetParamText (aboutStr);
	        //   (void) Alert (aboutAlrt, nil);
	        //   return 0;
	
	             Handle hResource;
	             ProcPtr pCode;
	
	             hResource = GetResource('INIT',1);   // load the resource
	             if (hResource != NULL)               // make sure it's loaded
	        {
	             HLock(hResource);                    // lock down the handle
	             pCode = _PvApplyFixup(hResource);    // get pointer to function
	             pCode();                             // call the code resource
	             HUnlock(hResource);
	        }
	
	        return 0;
	        }
	
	3. Build the MYSKEL sample project, and copy the executable to the Macintosh.
	  Give the remote executable path and file name. For example:
	
	  Macintosh HD:Testing:MYSKEL
	
	4. Use a Macintosh resource editor application such as ResEdit to copy the INIT
	  resource in the SACODE file to the MYSKEL executable.
	
	5. Execute the MYSKEL program, and click About on the Help menu. The code
	  resource will be executed, resulting in a series of five beeps.
	
	Additional query words: kbinf 2.00
	
	======================================================================
	Keywords          :  
	Technology        : kbVCsearch kbHWMAC kbOSMAC kbAudDeveloper kbVCXDev400Mac
	
	=============================================================================
	

{% endraw %}
