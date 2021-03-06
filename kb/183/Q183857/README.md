---
layout: page
title: "Q183857: WD97: Save As HTML Command Missing from File Menu"
permalink: /kb/183/Q183857/
---

## Q183857: WD97: Save As HTML Command Missing from File Menu

{% raw %}

	Article: Q183857
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): word97 kbwdinternet
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	The "Save As HTML" command is missing from the File menu. Additionally, "HTML
	document (*.htm,*.html,*.htx)" is not an available option when you try to save
	your Web page.
	
	NOTE: This problem may occur even when the HTML converter is already installed
	and the Html32.cnv file is present in the TextConv folder.
	
	CAUSE
	=====
	
	The HTML converter may not be installed or may not be correctly registered.
	
	RESOLUTION
	==========
	
	Use one or more of the following methods appropriate for your situation.
	
	Method 1: Install the Web Page Authoring Component
	--------------------------------------------------
	
	To resolve this issue, install the Web Page Authoring component in Microsoft
	Office 97. To do this, follow these steps:
	
	1. Quit all Office programs.
	
	2. Click the Start button, point to Settings, and then click Control Panel.
	
	3. In Control Panel, double-click the Add/Remove Programs icon.
	
	4. On the Install/Uninstall tab, click to select Microsoft Office 97. (If you
	  are using a stand-alone version of one of the Office programs, click to
	  select the appropriate product in the list.) Then, click Add/Remove.
	
	5. Follow the directions provided in the Setup dialog boxes.
	
	For more information about starting Microsoft Office Setup, click the Office
	Assistant, type "Installing Microsoft Office" (without quotation marks), click
	Search, and then click to select the "Install or remove individual components"
	topic.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Method 2: Re-register Word or Office Setup with the /y Switch
	-------------------------------------------------------------
	
	To resolve this issue, try running Setup /y for Word or Office to repair registry
	corruption.
	
	To run Setup with the /y switch, follow these steps:
	
	1. Insert the Word or Office CD into the CD drive. If you installed Word or
	  Office from floppy disks, insert the Setup Disk 1 in your computer's floppy
	  disk drive.
	
	2. Click the Start button and then click Run.
	
	3. In the Open box, type the following
	
	  <drive>:\setup /Y
	
	  where <drive> is the letter of the drive that contains the CD or Setup
	  Disk 1.
	
	4. Click OK.
	
	5. Click Reinstall.
	
	  This will re-register Word (and all Office programs, if you run Office Setup).
	
	If these steps don't correct the problem, you may need to remove Word, run
	OffClean found on the Microsoft Office CD within the ValuPack folder and then
	reinstall Word.
	
	For additional information about OffClean, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q158098 OFF97: Setup May Remove Older Components
	
	
	Method 3: Modify the Windows Registry
	-------------------------------------
	
	This problem can be resolved by manually editing the Windows Registry to add the
	correct entries to the Export and Import keys.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	1. Quit all Windows programs.
	
	2. On the Start menu, click Run.
	
	3. Type "Regedit" (without the quotation marks) in the Open box, and then click
	  OK.
	
	4. Modify the Export key using the following steps:
	
	  a. Open the registry to the following key:
	
	        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Text
	        Converters\Export
	
	  b. With the Export key selected, point to New on the Edit menu and then click
	     Key.
	
	  c. Type "HTML" (without the quotation marks) as the new key name and then
	     press ENTER.
	
	  d. With the HTML key selected, point to New on the Edit menu and then click
	     String Value.
	
	  e. Type "Extensions" (without the quotation marks) as the new string name and
	     then press ENTER.
	
	  f. With the Extensions string selected, click Modify on the Edit menu.
	
	  g. Type "html htm htx" (without the quotation marks) into the Value data box
	     and then click OK.
	
	  h. With the HTML key selected, point to New on the Edit menu and then click
	     String Value.
	
	  i. Type "Name" as the new string name and then press ENTER.
	
	  j. With the Name string selected, click Modify on the Edit menu.
	
	  k. Type "HTML Document" (without the quotation marks) and then click OK.
	
	  l. With the HTML key selected, point to New on the Edit menu and then click
	     String Value.
	
	  m. Type "Path" (without the quotation marks) and then press ENTER.
	
	  n. With the Path string selected, click Modify on the Edit menu.
	
	  o. Type the full path to the Html32.cnv converter into the Value Data box and
	     then click OK.
	
	     NOTE: The default path to the Html32.cnv converter file is the following:
	
	  C:\Program Files\Common Files\Microsoft Shared\TextConv\Html32.cnv
	
	5. Modify the Import key using the following steps:
	
	  a. Open the registry to the following key:
	
	HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Text Converters\Import
	
	  b. With the Import key selected, point to New on the Edit menu and then click
	     Key.
	
	  c. Type "HTML" (without the quotation marks) as the new key name and then
	     press ENTER.
	
	  d. With the HTML key selected, point to New on the Edit menu and then click
	     String Value.
	
	  e. Type "Extensions" (without the quotation marks) as the new string name and
	     then press ENTER.
	
	  f. With the Extensions string selected, click Modify on the Edit menu.
	
	  g. Type "html htm htx otm asp" (without the quotation marks) into the Value
	     data box and then click OK.
	
	  h. With the HTML key selected, point to New on the Edit menu and then click
	     String Value.
	
	  i. Type "Name" as the new string name and then press ENTER.
	
	  j. With the Name string selected, click Modify on the Edit menu.
	
	  k. Type "HTML Document" (without the quotation marks) and then click OK.
	
	  l. With the HTML key selected, point to New on the Edit menu and then click
	     String Value.
	
	  m. Type "Path" (without the quotation marks) and then press ENTER.
	
	  n. With the Path string selected, click Modify on the Edit menu.
	
	  o. Type the full path to the Html32.cnv converter into the Value Data box and
	     then click OK.
	
	     NOTE: The default path to the Html32.cnv converter file is the following:
	
	  C:\Program Files\Common Files\Microsoft Shared\TextConv\Html32.cnv
	
	After you restart Word, Save as HTML should now show on the File menu and the
	HTML converter should be available when you click Save (Save As) on the File
	menu.
	
	Method 4: Remove All, Run Eraser and then Reinstall
	---------------------------------------------------
	
	To resolve this issue, do the following steps:
	
	1. Run Setup for Word or Office and Remove All.
	
	2. Run the Eraser 97 utility to remove all remaining Office/Word files and to
	  delete corresponding registry entries.
	
	  For more information about the Eraser utility, please see the following
	  article in the Microsoft Knowledge Base:
	
	  Q176823 OFF97: Utility to Completely Remove Remaining Office 97 File
	
	3. Re-install either Word 97 or Office 97 for Windows.
	
	Additional query words: 8.0 authoring conversion convert hypertext
	
	======================================================================
	Keywords          : word97 kbwdinternet 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
