---
layout: page
title: "Q75786: RESTORE Command Requires Path and Filename of Files to Restore"
permalink: /kb/075/Q75786/
---

## Q75786: RESTORE Command Requires Path and Filename of Files to Restore

{% raw %}

	Article: Q75786
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.3,4.x,5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.3, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If use the RESTORE command and specify the drives only (for example, RESTORE A:
	C:), the following error message is displayed:
	
	  WARNING! No files were found to restore.
	
	MORE INFORMATION
	================
	
	The RESTORE command must have the complete path and filename of the file(s) that
	are to be restored. The RESTORE command restores the file(s) and directories
	just as they were before the BACKUP. Wildcards and switches may be used as
	substitutes.
	
	The following examples illustrate different wildcards and switches that may be
	used with the RESTORE command, and the results of the given command. The drives
	used in the examples may be replaced by any other legitimate drive (including a
	RAM drive).
	
	RESTORE A: C:\*.*
	-----------------
	
	  Restores files that were backed up from the root directory. Note: This
	  command will return the following error message if only subdirectories were
	  backed up:
	
	  WARNING! No files were found to restore.
	
	RESTORE A: C:\ /S
	-----------------
	
	  Restores all subdirectories and their files from the given backup.
	
	RESTORE A: C:\*.* /S
	--------------------
	
	  Restores all files in root directory and all files in subdirectories for the
	  given backup.
	
	RESTORE A: C:
	-------------
	
	  Restores all files backed up from the current directory of drive C.
	
	REFERENCES
	==========
	
	"Microsoft MS-DOS User's Guide and Reference," version 5.0, pages 555-557.
	
	"Microsoft MS-DOS User's Guide," version 4.01, pages 119-120.
	
	Additional query words: 6.22 3.30 4.00 4.01 4.01a 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS400 kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.3,4.x,5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
