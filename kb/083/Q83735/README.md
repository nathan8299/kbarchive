---
layout: page
title: "Q83735: LVMD.386 and LMOUSE.DRV Not Installed with Windows 3.1"
permalink: /kb/083/Q83735/
---

## Q83735: LVMD.386 and LMOUSE.DRV Not Installed with Windows 3.1

{% raw %}

	Article: Q83735
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When Express Setup is used to upgrade Microsoft Windows 3.0a to Microsoft
	Windows 3.1 or 3.11 on a system with a Logitech mouse, the LMOUSE.DRV file and
	the virtual driver file LVMD.386 are not installed.
	
	This article describes the procedure for installing these drivers.
	
	MORE INFORMATION
	================
	
	To install these drivers:
	
	1. At the MS-DOS command prompt, copy EXPAND.EXE from Disk 3 of the Windows
	  setup disks to the root directory on drive C. For example, if disk 3 is in
	  drive A, you would type the following and press ENTER:
	
	  copy a:expand.exe c:\
	
	2. Delete the LMOUSE.DRV file in the Windows\SYSTEM subdirectory. To do this,
	  use the MS-DOS CD command to change to the Windows\SYSTEM subdirectory, then
	  issue the MS-DOS DEL command. The following is an example (press ENTER at the
	  end of each line):
	
	        cd\windows\system
	        del lmouse.drv
	
	3. If you are using 1.2 MB or 1.44 MB Windows setup disks, insert Disk 2. If you
	  are using 720K disks insert Disk 4.
	
	4. Type the following commands (press ENTER at the end of each line):
	
	  expand a:lmouse.dr_ c:\windows\system\lmouse.drv
	
	  expand a:lvmd.38_ c:\windows\system\lvmd.386
	
	5. Edit the SYSTEM.INI file with a standard ASCII text editor (such as Notepad
	  or the Microsoft MS-DOS version 5.0 Editor) and make sure the following two
	  lines exist under the correct section header.
	
	  The following line should already exist:
	
	        [boot]
	        MOUSE.DRV=LMOUSE.DRV
	
	  The following line replaces MOUSE=*VMD:
	
	        [386Enh]
	        MOUSE=LVMD.386
	
	NOTE: If you run Setup from inside of Windows to switch from any available mouse
	selection and switch to Logitech Mouse, then LMOUSE.DRV and LVMD.386 are copied
	to your system from the Windows disks. LMOUSE.COM is not copied. LMOUSE.COM is
	necessary for mouse support for non-Windows-based applications and should be
	loaded before starting Windows.
	
	Use the following command line to expand LMOUSE.COM from the Windows disks:
	
	  expand a:\lmouse.co_ c:\windows\lmouse.com
	
	Additional query words: 3.10 3.11 upgrade update set up
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
