---
layout: page
title: "Q143370: Explorapedia Nature: Setup Runs Each Time You Insert the CD"
permalink: /kb/143/Q143370/
---

## Q143370: Explorapedia Nature: Setup Runs Each Time You Insert the CD

{% raw %}

	Article: Q143370
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.2 (UK only)
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Explorapedia series: World of Nature for Windows, version 1.2 (UK only) 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, you should first make a backup copy of the
	registry files (System.dat and User.dat). Both are hidden files in the
	Windows folder.
	
	SYMPTOMS
	========
	
	Every time you insert the Explorapedia World of Nature (Nature) compact disc
	into the CD-ROM drive, Nature Setup runs.
	
	This occurs with version Nature version 1.2 (United Kingdom only) installed on a
	computer running Windows 95/98.
	
	RESOLUTION
	==========
	
	To stop Setup from running every time you insert the compact disc, use the
	following instructions.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	For information about how to edit the registry, view the Changing Keys And Values
	online Help topic in Registry Editor (Regedit.exe). Note that you should make a
	backup copy of the registry files (System.dat and User.dat) before you edit the
	registry.
	
	1. Click Start, and then click Run.
	
	2. In the Open: box, type the following line, and then click OK:
	
	  " regedit " (without the quotation marks)
	
	3. Click the plus sign (+) next to the HKEY_LOCAL_MACHINE folder.
	
	4. Click the plus sign next to the SOFTWARE folder.
	
	5. Click the plus sign next to the Microsoft folder.
	
	6. Click the plus sign next to the Windows folder.
	
	7. Click the plus sign next to the CurrentVersion folder.
	
	8. Click the plus sign next to the App Paths folder.
	
	9. Click the App Paths folder.
	
	10. On the Edit menu at the top of the Registry Editor window, click New Key.
	
	11. Type the following as the name of the new folder, and then press ENTER:
	
	  " PEOPLE.EXE " (without the quotation marks)
	
	12. On the right side of the split screen, double-click the word (Default).
	
	13. A dialog box should appear with the title "Edit String" (without the
	  quotation marks).
	
	14. In the Value data box, type the following:
	
	  " C:\Program Files\Microsoft Kids\NatureZ\NATURE.EXE " (without the quotation
	  marks)
	
	  where C is the hard drive where you installed Nature.
	
	15. Click OK.
	
	16. On the Registry menu, click Exit.
	
	The Windows Autorun feature should now work successfully with Explorapedia
	Nature.
	
	MORE INFORMATION
	================
	
	In summary, what you need to do in Regedit is enter the path to Nature.exe as
	the (Default) value under the PEOPLE.EXE key in the App Paths section of the
	registry.
	
	
	Microsoft has confirmed this to be a problem in Explorapedia Nature for Windows
	95, version 1.2 (UK only).
	
	
	Additional query words: 1.20 mskids kids tad series explore kbmm world people nature multimedia multi-media multi 32-bit bundle easyball easy ball auto
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeMMsearch kbZNotKeyword2 kbExplorapediaNature120
	Version           : WINDOWS:1.2 (UK only)
	
	=============================================================================
	

{% endraw %}
