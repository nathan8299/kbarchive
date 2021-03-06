---
layout: page
title: "Q202063: SMS: Forced Disconnect Not Available on NW Distribution Servers"
permalink: /kb/202/Q202063/
---

## Q202063: SMS: Forced Disconnect Not Available on NW Distribution Servers

{% raw %}

	Article: Q202063
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2,2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbDespooler kbOSNovell
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.2, 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a client has a file open when a distribution process tries to copy files to
	the target distribution servers, the distribution may fail or go into an endless
	retry cycle.
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	With Systems Management Server 1.2, a registry option was introduced to force a
	disconnection of the client so the distribution phase could complete. The
	registry entry is located at:
	
	  
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Components\SMS_Despooler
	
	The "Use Forced Disconnect" parameter should have a value of 1.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	MORE INFORMATION
	================
	
	This setting is still available in Systems Management Server 2.0. However, this
	setting only applies to Windows NT distribution servers, and not to Novell
	NetWare distribution servers.
	
	For additional information about how to force disconnect Windows NT distribution
	servers, please see the following article in the Microsoft Knowledge Base:
	
	  Q128458 SMS Despooler Does Not Support Forced Installation and Upgrade
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: prodsms sms20 novel novell
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbDespooler kbOSNovell 
	Technology        : kbSMSSearch kbSMS120 kbSMS200
	Version           : winnt:1.2,2.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
