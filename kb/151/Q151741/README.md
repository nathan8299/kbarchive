---
layout: page
title: "Q151741: Compressed Drives in Compatibility Mode After Compact Setup"
permalink: /kb/151/Q151741/
---

## Q151741: Compressed Drives in Compatibility Mode After Compact Setup

{% raw %}

	Article: Q151741
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): diskmem win95 kbDiskMemory
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Plus! for Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After installing Windows 95 using the Compact option onto a compressed drive
	that has low free disk space and uses real-mode compression or disk drivers, the
	Performance tab in System properties may indicate that the disk compression and
	file system are using MS-DOS Compatibility mode.
	
	CAUSE
	=====
	
	A forced Compact installation of Windows 95 does not install 32-bit disk
	compression drivers.
	
	RESOLUTION
	==========
	
	To enable 32-bit disk compression and file system drivers on a computer using
	DoubleSpace or DriveSpace compression, perform the following steps.
	
	NOTE: This resolution requires approximately 1.4 MB of free hard disk space.
	
	1. In Control Panel, double-click the Add/Remove Programs icon.
	
	2. On the Windows Setup tab, click Disk Tools, and then click Details.
	
	3. Click the Disk Defragmenter and Disk Compression check boxes to select them,
	  and then click OK.
	
	4. Click Close.
	
	5. When you are prompted to restart the computer, do so.
	
	To enable 32-bit disk compression and file system drivers on a computer using
	DriveSpace 3 compression, extract the Drvspacx.vxd file from the Plus_01.cab
	cabinet file on your original Microsoft Plus! CD-ROM or disk 1 to the
	Windows\System\Iosubsys folder on the hard disk.
	
	For additional information about using the Extract tool, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q129605 How to Extract Original Compressed Windows Files
	
	MORE INFORMATION
	================
	
	Under normal circumstances Windows 95 Setup detects the presence of the
	Dblspace.bin or Drvspace.bin file in the root folder and includes DriveSpace
	disk compression in the installation.
	
	When the hard disk is low on free space, Setup forces a special Compact
	installation. In this forced Compact installation, unnecessary components are
	bypassed by Setup that would be available in an ordinary Compact installation
	(including the protected mode compression drivers Mrci2.vxd and Drvspace.sys).
	
	For more information about installed components and Setup options, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q123876 Installed Components for Typical, Compact, or Portable Setup
	
	======================================================================
	Keywords          : diskmem win95 kbDiskMemory 
	Technology        : kbWin95search kbGamesSearch kbPlusSearch kbZNotKeyword3 kbPlus95
	Version           : 95
	
	=============================================================================
	

{% endraw %}
