---
layout: page
title: "Q173882: Netlogon Synchronization Errors"
permalink: /kb/173/Q173882/
---

## Q173882: Netlogon Synchronization Errors

{% raw %}

	Article: Q173882
	Product(s): Microsoft Windows NT
	Version(s): 2000,2000 SP1,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 29-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows versions 2000, 2000 SP1 Advanced Server 
	- Microsoft Windows versions 2000, 2000 SP1 Server 
	- Microsoft Windows 2000 Datacenter Server 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Netlogon creates many errors that are recorded in the event log, which
	eventually fills or wraps the log.
	
	MORE INFORMATION
	================
	
	The Netlogon.chg file is located on all domain controllers, but is used only by
	the primary domain controller (PDC) to keep track of changes made to the
	security databases. All changes to the security databases are recorded in this
	log file, along with the serial number of the change. Each of the three security
	databases maintains a separate serial number, which is incremented once for each
	change. When a backup domain controller (BDC) requests a particular change from
	the PDC, the PDC checks the change log to determine which changes need to be
	sent.
	
	Specific Events and Errors
	--------------------------
	
	The following events may be recorded on the BDC:
	
	  Event ID: 5717
	  Source: NETLOGON
	  Type: Information
	  The full synchronization replication of the LSA database from the primary
	  domain controller \\<DOMAIN CONTROLLER> completed successfully.
	
	  Event ID: 5716
	  Source: NETLOGON
	  Type: Warning
	  The partial synchronization replication of the SAM database from the primary
	  domain controller <DOMAIN CONTROLLER> failed with the following error:
	
	  <THERE IS NO ERROR REPORTED>
	
	  The Data section contains c0000134 (Words) or 34 01 00 c0 (Bytes.); the
	  c0000134 indicates STATUS_SYNCHRONIZATION_REQUIRED.
	
	The following events may be reported on the PDC:
	
	  Event ID: 5713
	  Source: NETLOGON
	  Type: Information
	  The full synchronization request from the server <SERVERNAME> completed
	  successfully. <X> object(s) has(have) been returned to the caller.
	
	  Event ID: 5712
	  Source: NETLOGON
	  Type: Warning
	  The partial synchronization request from the server <SERVERNAME> failed
	  with the following error:
	
	  <THERE IS NO ERROR REPORTED>
	
	Trying to promote a BDC to a PDC may cause the following pop-up window message to
	stay on the screen indefinitely:
	
	"Synchronizing <BDC> with its primary"
	
	The following event log error may be generated:
	
	  Event ID: 5705
	  Source: NETLOGON
	  Type: Error
	  The change log cache maintained by the Netlogon Service for database changes
	  is corrupted. The Netlogon service is resetting the change log.
	
	These events can be caused when Windows NT fails to update the
	%SystemRoot%\Netlogon.chg file on the PDC. This may occur for any of the
	following reasons:
	
	- The Read-Only attribute could be set.
	
	- The netlogon.chg file could be corrupted.
	
	- The permissions for the system account could be insufficient for that file;
	  they should be at least RWXD.
	
	Resolving the Problem
	---------------------
	
	If the Netlogon.chg file has been corrupted, you may need to delete or rename the
	file. However, this file is always in use by the system.
	
	To delete (reset) the Netlogon.chg file on an NTFS partition, use the following
	steps:
	
	1. Open Windows Explorer, and then navigate to the %systemroot% folder.
	
	2. Right-click the Netlogon.chg file, and then click Properties.
	
	3. Click the Security tab.
	
	4. Click to clear the "Allow inheritable permissions from parent to propagate to
	  this object" check box, and then click OK.
	
	5. In the Security dialog box, click Copy to copy the existing inheritable
	  permissions to this object.
	
	6. Click the System account, click "Deny - Full Control" to change all of the
	  permissions to Deny, and then click OK.
	
	7. Restart the computer. After you log on to the computer, delete the
	  Netlogon.chg file.
	
	8. Restart the computer again. When you log on the computer, the Netlogon.chg
	  file is rebuilt automatically.
	
	To delete (reset) the Netlogon.chg file on a FAT partition, use the following
	steps:
	
	1. Start the system using MS-DOS, and then delete the %SystemRoot%\Netlogon.chg
	  file.
	
	2. Restart using Windows NT. The file will be recreated at startup.
	
	Additional query words: continuous repeated alternate server user manager forever 340100c0 warning informational blue yellow 4 A win2000
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000DataServ kbwin2000DataServSearch kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbwin2000ServSearch kbwin2000Search kbWinNTS351search kbWinAdvServSearch kbWinDataServSearch kbWin2000AdvServSP1 kbwin2000ServSP1
	Version           : :2000,2000 SP1,3.51,4.0
	Hardware          : x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
