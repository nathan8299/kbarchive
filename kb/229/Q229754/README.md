---
layout: page
title: "Q229754: XFOR: Web 3 cc:Mail Migration Wizard Does Not Migrate PAB"
permalink: /kb/229/Q229754/
---

## Q229754: XFOR: Web 3 cc:Mail Migration Wizard Does Not Migrate PAB

{% raw %}

	Article: Q229754
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After running the Web 3 cc:Mail Migration Wizard, Personal Address Book (PAB)
	entries are not migrated to the Exchange Server mailbox. Surprisingly, there are
	also no errors in the event log to indicate that there was a problem during the
	migration.
	
	CAUSE
	=====
	
	The incorrect version of Import.exe/Export.exe may have been used by the
	Migration Wizard. To migrate a DB8 Post Office, the Migration Wizard requires
	that the version of the Import.exe/Export.exe be 8.x or later. However, to be
	able to extract the PAB information, Import.exe/Export.exe has to be 8.3.x or
	later.
	
	RESOLUTION
	==========
	
	Check the following:
	
	1. Make sure that there is only one copy of the Import.exe/Export.exe files on
	  the computer performing the migration. In general, these files will be in the
	  Winnt or Winnt\System32 directory.
	
	2. Run "Export /?" (without the quotation marks) to get the version information.
	  Make sure that it is 8.3.x or later.
	
	3. Make sure that the version of the Migration Wizard is the most recent one. To
	  do this, bring up the property of the Mailmig.exe file, and check that the
	  version of this file is 5.5.2543.0 or later. This file can be found in the
	  Exchsrvr\Bin directory.
	
	Additional query words: PAB, SMTP, fails to migrate
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
