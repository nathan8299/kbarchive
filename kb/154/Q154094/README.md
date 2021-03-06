---
layout: page
title: "Q154094: Using Iomega ATAPI Zip Drives with Windows NT"
permalink: /kb/154/Q154094/
---

## Q154094: Using Iomega ATAPI Zip Drives with Windows NT

{% raw %}

	Article: Q154094
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbfile kbhw kbWinNT400sp4fix kbHardware
	Last Modified: 21-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Windows NT cannot access the disk in the ATAPI version of an Iomega Zip drive.
	
	CAUSE
	=====
	
	Windows NT identifies the ATAPI version of the Iomega Zip drive as a floppy disk
	drive and assigns it the first available floppy disk drive letter (usually B).
	This problem does not occur with the IDE version of the Iomega Zip drive as
	Windows NT properly identifies it.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	For your convenience, the English version of this post-SP3 hotfix has been posted
	to the following Internet location. However, Microsoft recommends that you
	install Windows NT 4.0 Service Pack 4 to correct this problem.
	
	ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/nt40/
	hotfixes-postSP3/zip-fix/
	
	NOTE: The above link is one path; it has been wrapped for readability.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	
	
	MORE INFORMATION
	================
	
	The simplest way to tell the difference between the IDE and ATAPI versions of
	the Zip drive is the fact that the IDE version works under Windows NT, while the
	ATAPI version does not work without the hotfix. You can also determine the type
	of Zip drive by examining the following registry key:
	
	HKEY_LOCAL_MACHINE\HARDWARE\DEVICEMAP\Scsi\ScsiPort0\ScsiBus0 \Target ID
	X\Logical Unit ID 0
	
	NOTE: The Target ID is 1 or 2 for devices on the primary EIDE channel and 3 or 4
	for devices on the secondary EIDE channel.
	
	In this key you see an Identifier value which includes information on the device
	such as the manufacturer, model number, and firmware revision. IDE and ATAPI Zip
	drives have identical information in this value except the firmware revision has
	a different format depending on the drive type:
	
	- The ATAPI drive firmware appears in the following format (note that the
	  letter follows the number):
	
	  IOMEGA ZIP 100 23.D
	
	- The IDE firmware number has the opposite format (note that the letter
	  precedes the number):
	
	  IOMEGA ZIP 100 B.29
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbhw kbWinNT400sp4fix kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
