---
layout: page
title: "Q318339: PRB: Event Log Errors in Index Server if Address Space Exhausted"
permalink: /kb/318/Q318339/
---

## Q318339: PRB: Event Log Errors in Index Server if Address Space Exhausted

{% raw %}

	Article: Q318339
	Product(s): Internet Information Server
	Version(s): 2.0,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Index Server versions 2.0, 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following event log errors may occur in Index Server when the 2-gigabyte
	(GB) process address space is exhausted:
	
	  5/10/01,5:49:58 PM,Ci,Error,CI Service ,4124,N/A,Server,Content index on
	  d:\catalog\catalog.wci is corrupt. Please shutdown and restart the Content
	  Index service (cisvc).
	
	  5/10/01,5:49:21 PM,Ci,Success Audit,CI Service ,4104,N/A,Server,Master merge
	  has been paused on d:\catalog\catalog.wci due to error 0x80070008. It will be
	  rescheduled later.
	
	CAUSE
	=====
	
	This behavior can occur because the dir files associated with each catalog must
	be mapped into contiguous virtual memory within the 2 GB of CiSvc process
	address space. If there is insufficient contiguous virtual memory, the catalog
	fails to start, and therefore the catalog is reported as corrupted and will be
	deleted.
	
	RESOLUTION
	==========
	
	You can use Microsoft Windows 2000 Advanced Server to expand the address space
	of CiSvc to 3 GB. To do this, follow these steps:
	
	1. Install Windows 2000 Advanced Server.
	
	2. Ensure that there is no disc in your computer's CD-ROM or DVD-ROM drive.
	
	3. Run the following command:
	
	  ipconfig /release
	
	4. Search drive C for Cisvc.exe. You will probably find a version in the
	  c:\winnt\servicepackfiles\i386 directory. Rename any copies that you find as
	  "Cisvc.bak" (without the quotation marks).
	
	5. Rename c:\winnt\system32\dllcache\cisvc.exe as
	  "c:\winnt\system32\dllcache\cisvc.bak" (without the quotation marks).
	
	6. Run the following command:
	
	  imagecfg -l c:\windows\system32\cisvc.exe
	
	  The time and date stamp should be updated to the time and date at which you
	  change the image. The Imagecfg.exe utility is included in Supplement One of
	  the Windows 2000 Resource Kit.
	
	7. Wait a few minutes, and then verify that the Cisvc.exe file in
	  c:\winnt\system32 is the updated binary with the correct time and date stamp.
	
	8. Modify the Boot.ini file to enable application memory tuning. To do this, add
	  the /3GB parameter to the ARC path, as follows:
	
	  multi(0)disk(0)rdisk(0)partition(2)\WINNT="Windows 2000 Advanced Server" /3GB
	
	9. Restart your computer.
	
	MORE INFORMATION
	================
	
	To detect this issue, add up the size of the dir files for each catalog. If the
	sum exceeds approximately 1.5 GB, the process virtual memory is most likely
	being exhausted.
	
	1.5 GB is a rough estimate taken from a reproduction of this issue. The number
	can, and will, vary depending on the sizes of the dir files, the order in which
	the catalogs load, and virtual memory usage and fragmentation.
	
	Dir files tend to become large when there are custom properties defined that
	contain a lot of unique words. The number of unique words can be determined on a
	per-catalog basis by using Perfmon to obtain the unique-keys value for each
	catalog.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbIdxServSearch kbAudDeveloper kbIdxServ200
	Version           : :2.0,3.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
