---
layout: page
title: "Q104393: How to Get Control Dimensions from VBGetControlProperty"
permalink: /kb/104/Q104393/
---

## Q104393: How to Get Control Dimensions from VBGetControlProperty

{% raw %}

	Article: Q104393
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.0,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 2.0, 3.0 
	- Microsoft Visual Basic Standard Edition for Windows, versions 2.0, 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows by example how to get the IPROP_STD_LEFT, IPROP_STD_TOP,
	IPROP_STD_WIDTH, and IPROP_STD_HEIGHT values using the VBGetControlProperty
	function.
	
	MORE INFORMATION
	================
	
	The IPROP_STD_LEFT, IPROP_STD_TOP, IPROP_STD_WIDTH, and IPROP_STD_HEIGHT
	properties are stored as floats. The following code shows how to call
	VBGetControlProperty to get these properties from a VBX and DLL. It is assumed
	that the standard property indexes found in VBAPI.H were used to build the
	control.
	
	  /* VBGetControlProperty is prototyped in vbapi.h */ 
	  #include <vbapi.h>
	
	  *** You also need to add "vbapi.lib" to the libraries in the makefile. ***
	
	   float fValue ;
	   int nRet ;
	
	    /* hctl would normally be passed in as a HCTL to the function using
	       VBGetControlProperty */ 
	    /* The third parameter must be the address of a float */ 
	   nRet = VBGetControlProperty(hctl, IPROP_STD_TOP, &fValue) ;
	
	Now fValue has the value of Top property for the hctl control.
	
	Additional query words: 2.00 3.00
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB300Search kbVB300 kbVB200
	Version           : :2.0,3.0
	
	=============================================================================
	

{% endraw %}
