---
layout: page
title: "Q191991: Error Message: Stop C0000142 (DLL Initialization Failed)"
permalink: /kb/191/Q191991/
---

## Q191991: Error Message: Stop C0000142 (DLL Initialization Failed)

{% raw %}

	Article: Q191991
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When Windows NT 4.0 starts, you may receive the following error message:
	
	  STOP C0000142 (DLL initialization failed)
	
	  Initialization of the dynamic link library c:<path>\user32.dll failed.
	  The process is terminating abnormally
	
	CAUSE
	=====
	
	This issue can occur if there are conflicting versions of the User32.dll and
	Gdi32.dll files.
	
	RESOLUTION
	==========
	
	To resolve this issue, replace the Gdi32.dll file in the %SystemRoot%\System32
	folder with the file that is included in the Windows NT 4.0 Service Pack that
	was loaded on the original installation. To verify, SP3 files display a modified
	date of 4/30/97 or 5/1/97, and SP4 files show a modified date of 10/15/98.
	
	Method 1
	--------
	
	If you have access to another Windows NT-based computer with Windows NT 4.0 SP3
	installed, copy the Gdi32.dll file from the other computer to the original
	computer. To do so, follow these steps:
	
	1. On the other computer, click Start, point to Programs, and then click Command
	  Prompt.
	
	2. Insert a formatted floppy disk into the floppy disk drive, type the following
	  line, and then press ENTER:
	
	  copy %SystemRoot%\system32\gdi32.dll <drive>:
	
	  Where <drive> is the drive letter of the floppy disk drive.
	
	3. Restart the original computer using any bootable floppy disk (such as an
	  MS-DOS boot disk, a Microsoft Windows 95 Emergency Boot disk, or a Microsoft
	  Windows 98 Startup disk), and then insert the floppy disk you used in step 2
	  in the floppy disk drive.
	
	  NOTE: For instructions about how to create a boot floppy disk, please consult
	  your operating system's documentation.
	
	4. Type the following lines, pressing ENTER after each line
	
	  ren %SystemRoot%\system32\gdi32.dll gdi32.old copy <drive>:\gdi32.dll
	  %SystemRoot%\system32\
	
	  Where <drive> is the drive letter of the floppy disk drive.
	
	5. Restart the computer.
	
	Method 2
	--------
	
	If you dual-boot Windows NT and Windows 95 or Windows 98 on your computer, follow
	these steps:
	
	1. Start Windows 95 or Windows 98.
	
	2. Click Start, point to Programs, and then click MS-DOS Prompt.
	
	3. Type the following line, and then press ENTER:
	
	  ren %SystemRoot%\system32\gdi32.dll gdi32.old
	
	4. If you have the SP3 CD-ROM, place it in the CD-ROM drive, type the following
	  line, and then press ENTER:
	
	  expand -r <drive>:\i386\gdi32.dll %SystemRoot%\system32\
	
	  Where <drive> is the drive letter of the CD-ROM drive. After you
	  complete this step, skip to step 7.
	
	5. If you downloaded SP3, you need to extract all files from the Nt4sp3_i.exe
	  file before you can obtain the Gdi32.dll file. To extract all files from the
	  Nt4sp3_i.exe file, consult the instructions in the "Downloading and
	  Extracting the Service Pack" section of the following article in the
	  Microsoft Knowledge Base:
	
	  Q152841Windows NT 4.0 Service Pack 3 Readme.txt File (40-bit)
	
	6. Type the following line, and then press ENTER:
	
	  copy <path>\gdi32.dll %SystemRoot%\system32\
	
	  Where <path> is the location of the SP3 files.
	
	7. Restart your computer.
	
	Method 3
	--------
	
	If you have Windows NT installed on an NTFS partition, follow these steps:
	
	1. Install Windows NT in a different folder on your hard disk, and then install
	  SP3.
	
	2. Copy the Gdi32.dll file from the %SystemRoot%\System32 folder in the new
	  Windows NT installation to the corresponding folder in the original
	  installation. To do so, type the following line, and then press ENTER:
	
	  copy %SystemRoot%\system32\Gdi32.dll <path>\system32
	
	  Where <path> is the original installation.
	
	3. Restart your computer to the original Windows NT installation.
	
	4. Remove the temporary Windows NT installation, and then delete any entries in
	  the Boot.ini file that are entered for that installation.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
