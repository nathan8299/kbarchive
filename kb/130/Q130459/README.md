---
layout: page
title: "Q130459: Adding TrueType, Raster, or Vector Fonts to System"
permalink: /kb/130/Q130459/
---

## Q130459: Adding TrueType, Raster, or Vector Fonts to System

{% raw %}

	Article: Q130459
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1,95; winnt:3.5,3.51
	Operating System(s): 
	Keyword(s): kbfile kbgraphic kbOSWinNT350 kbOSWinNT351 kbSDKWin32 kbOSWin95 kbDSupport
	Last Modified: 16-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	- Microsoft Win32 Application Programming Interface (API), included with:
	   - Microsoft Windows NT Server versions 3.5, 3.51 
	   - Microsoft Windows NT Workstation versions 3.5, 3.51 
	   - Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	FONTINST is a sample application in the Microsoft Software Library that
	demonstrates how to programmatically add a TrueType, raster, or vector font to
	the system.
	
	When working with a TrueType font file (.ttf file), FONTINST creates a .fot file
	and moves the specified .ttf file to the Windows system directory. For a raster
	or vector font file (.fon file), FONTINST moves the .fon file to the Windows
	system directory. After the font file has been moved to the system directory,
	FONTINST adds the font to the system by using the AddFontResource() API. Then it
	adds font information to the [fonts] section of the Win.ini file so that the
	font is automatically loaded every time Windows starts. For example, the
	following line is added to the Win.ini file when FONTINST adds the Arial.ttf
	file to the system:
	
	     Arial (TrueType)=ARIAL.FOT
	
	FONTINST also demonstrates how to retrieve the facename of a font given a .ttf or
	.fon file. In the case of a TrueType font, FONTINST opens up the file and reads
	the naming table of the .ttf file. FONTINST also shows how to read the FONTINFO
	structure (as described on pages 49-50 of the "Microsoft Windows Software
	Development Kit: Programmer's Reference, Volume 4: Resources") of a .fon file.
	The facename of a font in a .fon file can also be found in this manner.
	
	After a font is installed by FONTINST, information about the font is displayed in
	the window. Information such as the TEXTMETRIC structure and font type, as well
	as sample font text, is displayed. Information added to the Win.ini file is also
	displayed in this window.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Software
	Library:
	
	  ~ FONTINST.EXE
	  (http://support.microsoft.com/download/support/mslfiles/FONTINST.EXE)
	
	For more information about downloading files from the Microsoft Software Library,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	
	Additional query words: softlib kbgraphic kbfile
	
	======================================================================
	Keywords          : kbfile kbgraphic kbOSWinNT350 kbOSWinNT351 kbSDKWin32 kbOSWin95 kbDSupport 
	Technology        : kbAudDeveloper kbSDKSearch kbWin32sSearch kbWin32API kbWinSDKSearch
	Version           : WINDOWS:3.1,95; winnt:3.5,3.51
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
