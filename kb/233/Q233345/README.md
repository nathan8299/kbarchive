---
layout: page
title: "Q233345: XFOR: Notes Connector Event ID 1: DXANOTES Failed to Initialize"
permalink: /kb/233/Q233345/
---

## Q233345: XFOR: Notes Connector Event ID 1: DXANOTES Failed to Initialize

{% raw %}

	Article: Q233345
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 06-JUN-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Exchange Server version 5.5, after you start the Exchange Connector
	for Lotus Notes service, Event ID 1 is constantly logged in the Event Viewer
	application log. Some of these events include the following description:
	
	  LME-NOTES-DXANOTES(020d)1 64002:error[Invalid configuration:failed to
	  initialize notes directory exchange agent].
	
	-or-
	
	  Default queue route of Q does not exist.
	
	If directory synchronization between Exchange Server and Lotus Notes is
	configured, it does not work, but mail flow functions correctly.
	
	CAUSE
	=====
	
	The Q directory is missing for %Exchsrvr%\Connect\Exchconn.
	
	RESOLUTION
	==========
	
	Open Windows NT Explorer and create the directory %Exchsrvr%\Connect\Exchconn
	\Q.
	
	As soon as you create the directory, the Exchange Connector for Lotus Notes
	service will automatically create the following Q subdirectories:
	
	  Archive
	  Badmif
	  Dxamex.in
	  DXAmex.out
	
	Restart the Exchange Connector for Lotus Notes service, and the Application Log
	events should stop, and directory replication will resume.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
