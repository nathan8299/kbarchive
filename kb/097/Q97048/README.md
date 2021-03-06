---
layout: page
title: "Q97048: HOWTO: Restore Corrupt or Deleted Visual C++ Group File"
permalink: /kb/097/Q97048/
---

## Q97048: HOWTO: Restore Corrupt or Deleted Visual C++ Group File

{% raw %}

	Article: Q97048
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:1.0,1.5; winnt:1.0,2.0,2.1,4.0,5.0
	Operating System(s): 
	Keyword(s): kbsetup kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500
	Last Modified: 10-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 1.0, 1.5, 2.0, 2.1, 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If the Microsoft Visual C++ (MSVC) program group in Microsoft Windows Program
	Manager becomes corrupted or if it is deleted, you can use the MSVC Setup
	program to restore the group.
	
	MORE INFORMATION
	================
	
	If you specify the /F option switch on the MSVC Setup command line, Setup does
	not copy any files. It only updates the MSVC group in Program Manager and the
	SYSTEM.INI and TOOLS.INI files. To create or restore the MSVC group, perform the
	following five steps:
	
	1. Insert Microsoft Visual C++ Disk 1 into a floppy disk drive or insert the
	  Microsoft Visual C++ CD into your CD-ROM drive. The following instructions
	  assume that this drive is drive X.
	
	2. In the Program Manager, choose Run from the File menu.
	
	3. If you are using Visual C++ for Windows 1.0 or 1.5 or Visual C++ 32-bit
	  Edition version 1.0, enter the following command line in the Run dialog box:
	
	  x:setup /F
	
	  Note: The "F" must be an uppercase letter.
	
	  In Visual C++ 2.0, the setup program does not accept the /F parameter. Use the
	  following command in the Run dialog box instead:
	
	  x:\msvc20\vcsetup /f
	
	  In Visual C++ 4.0, the AUTOVC.EXE program does not accept any parameters.
	  Instead, use the following command line in the Run dialog box:
	
	  x:\msdev\setup /F
	
	  In Visual C++ 5.0, use the following command line in the Run dialog box:
	
	  x:\DevStudio\Vc\setup /F
	
	4. Click OK.
	
	5. Specify information about your system according to the instructions in the
	  Setup program. When Setup runs, it does not copy any files but it does create
	  the appropriate program groups and icons. Toward the end of the process,
	  accept the default option to write the SYSTEM.INI and TOOLS.INI files to a
	  different name if asked (to prevent the new information from overwriting the
	  current files). When Setup is complete, it is not necessary to restart
	  Windows.
	
	Even though Setup does not copy any files, it displays every screen (checking for
	available disk space, and so on). Furthermore, the Visual C++ for Windows NT
	Setup program prompts the user to register environment variables (which is one
	method to register the environment variables if you have not already done so).
	
	Additional query words: icon
	
	======================================================================
	Keywords          : kbsetup kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbvc150 kbvc100 kbVC500 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : WINDOWS:1.0,1.5; winnt:1.0,2.0,2.1,4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
