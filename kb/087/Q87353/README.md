---
layout: page
title: "Q87353: Using Publisher's PowerPak with Windows 3.1"
permalink: /kb/087/Q87353/
---

## Q87353: Using Publisher's PowerPak with Windows 3.1

{% raw %}

	Article: Q87353
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses some of the common problems you may experience if you use
	Atech Software's Publisher's PowerPak, a real-time font-scaling package, with
	Microsoft Windows 3.1:
	
	- Version 1.57 or later required
	
	- Random general protection (GP) faults after installing Fast Fonts over
	  Publisher's PowerPak
	
	- PowerPak Options button unavailable in Notepad and Write
	
	- Files and settings installed by PowerPak version 1.2
	
	NOTE: Atech Software is no longer in business.
	
	MORE INFORMATION
	================
	
	Recommended Publisher's PowerPak Version: 1.57
	----------------------------------------------
	
	Atech Software recommends using version 1.57 or later for full compatibility with
	Windows 3.1.
	
	GP Faults
	---------
	
	Random general protection (GP) faults may occur in Windows 3.1 after Fast Fonts
	is installed over Atech PowerPak. Atech Fast Fonts changes the display.drv= line
	in the [boot] section of the SYSTEM.INI file to the following:
	
	  display.drv = FFSCR.DRV
	
	This driver is designed for all kinds of video cards and it is needed to support
	true WYSIWYG.
	
	To resolve this problem, delete PPAK.DRV from the WINDOWS\SYSTEM directory and
	restart Windows.
	
	You can also manually change the display.drv= line in the SYSTEM.INI file to use
	the Windows 3.1 default video driver, but the display quality of the fonts will
	be affected.
	
	Publisher's PowerPak Options Button Unavailable in Notepad and Write
	--------------------------------------------------------------------
	
	When using Publisher's PowerPak version 1.2 with Windows 3.1, the Options button
	under File Printer Setup is unavailable (dimmed) in Notepad and Write. The
	Option dialog box can be accessed from other applications or by choosing the
	Printers icon from Control Panel.
	
	
	Files and Settings Installed by Publisher's PowerPak
	----------------------------------------------------
	
	  Application Name:   Publisher's PowerPak version 1.2
	  Manufacturer:       Atech Software
	  RAM needed:         1 MB
	  Disk space needed:  1 MB
	
	Changes made to MS-DOS files: n/a
	
	Changes made to Windows files:
	
	     SYSTEM.INI:
	     [boot]
	     display.drv=ppakvga.drv
	     [boot.description]
	     display.drv=ppakvga.drv
	
	     WIN.INI:
	     [PrinterPorts]
	     Publishers PowerPak=POWERPAK, LPT1:, 15, 45
	     [devices]
	     Publishers PowerPak=POWERPAK, None
	     [POWERPAK]
	     config=POWERPAK.CFG
	
	Files copied to the Windows root directory:
	
	     PPAKVGA.DRV
	     POWERPAK.DRV
	
	Files copied to the new Windows POWERPAK subdirectory:
	
	     SCREEN.CFG
	     POWERPAK.PFP
	     STUB
	     PRINTER.DAT
	     DIXON.FF1
	     MARIN.FF1
	     COBB.FF1
	     README.COM
	
	Publisher's PowerPack is manufactured by a vendor independent of Microsoft; we
	make no warranty, implied or otherwise, regarding this product's performance or
	reliability.
	
	Additional query words: gpf 3.10 3.11 powerpack power pack pak 3rdparty FFPRN.DRV
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
