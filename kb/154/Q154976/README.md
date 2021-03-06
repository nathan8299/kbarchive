---
layout: page
title: "Q154976: Error Message Running Jet Database Engine Stress Test"
permalink: /kb/154/Q154976/
---

## Q154976: Error Message Running Jet Database Engine Stress Test

{% raw %}

	Article: Q154976
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): kberrmsg kbhw kbpolicy win95 kbHardware kbgraphxlinkcriticalkbfixlist
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are running a program that causes a large number of writes to occur
	very rapidly to an IDE drive, you may receive the following error message on a
	blue screen:
	
	  Disk Write Error
	  Unable to write to disk in drive <x>:
	  Data or files may be lost
	
	You may be able to recover from this error by pressing a key to remove the error
	message and retry the write. The operation typically continues, although
	additional errors may occur until the operation is finished.
	
	CAUSE
	=====
	
	If a program generates a large number of disk writes very quickly, a timing
	problem involving the IDE disk driver and the cache may occur, resulting in the
	error message.
	
	This symptom has been reported to occur with a hard disk stress test using the
	Microsoft Jet database engine that is included with the current versions of
	Microsoft Visual Basic, Microsoft Office, and Microsoft Access.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem immediately, download the fix as instructed below or
	contact Microsoft Product Support Services to obtain the fix. For a complete
	list of Microsoft Product Support Services phone numbers and information on
	support costs, please go to the following address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The following file is available for download from the Microsoft Download Center:
	
	  Download Remideup.exe now
	  (http://download.microsoft.com/download/win95upg/update2/1/w95/en-us/remideup.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. After it is posted, the file is housed on
	secure servers that prevent any unauthorized changes to the file.
	
	The following files are installed by Remideup.exe:
	
	  File name     Version    Date/Time       Size    Destination folder
	  ------------------------------------------------------------------------
	  Esdi_506.pdr  4.00.1116  8/25/97 11:16a  24,426  Windows\System\Iosubsys
	  Voltrack.vxd  4.00.954   3/6/96 9:54a    18,518  Windows\System\Iosubsys
	
	NOTE: The Voltrack.vxd file is installed on Windows 95 computers only. This file
	is not installed on computers running OSR2.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	For additional information about issues resolved by updates to this component,
	please see the following articles in the Microsoft Knowledge Base:
	
	  Q171353 Computer with Ultra DMA IDE Controller May Hang
	
	  Q161642 Auto Insert Notification May Prevent Automatic Suspend
	
	  Q160800 "Fatal Exception Error" with Iomega IDE Zip Drives
	
	  Q154436 Errors Accessing Hard Disk with Spin-Down Enabled
	
	  Q154435 Windows 95 IDE Support for SMART, DMA, and ATAPI Tape Drives
	
	  Q153471 Problems with Removable IDE Drives in Windows 95
	
	Additional query words: vb script
	
	======================================================================
	Keywords          : kberrmsg kbhw kbpolicy win95 kbHardware kbgraphxlinkcritical kbfixlist
	Technology        : kbWin95search kbZNotKeyword3
	Version           : :95
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
