---
layout: page
title: "Q224992: Maintaining Transactional Integrity with OPLOCKS"
permalink: /kb/224/Q224992/
---

## Q224992: Maintaining Transactional Integrity with OPLOCKS

{% raw %}

	Article: Q224992
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Under extreme conditions, some multiuser database applications that use a common
	data store over a network connection on a file server may experience
	transactional integrity issues or corruption of the database files and/or
	indexes stored on the server. This typically applies to some so-called "ISAM
	style", or "record oriented" multiuser database applications, not to a
	client/server relational system like SQL Server.
	
	CAUSE
	=====
	
	If a multiuser or single user database application accesses a common data store
	on a Windows NT file server using opportunistic locks (or OPLOCKS), it is
	possible for a given user to cache partial transactions on the client systems
	hard drive. This is a performance enhancement to the Windows client redirector
	to reduce network file I/O between the client and server. The data being cached
	on the client redirector is later written back to the server. However, in some
	cases, a client system may stop responding (hang), do a hard reboot, lose its
	network connection to the server, or experience any number of other technical
	difficulties. In such cases, the content of the local cache that has not yet
	been written to the server can be lost. As a result, the transaction integrity
	of the database structures on the server is compromised and the data on the file
	server can become corrupted.
	
	RESOLUTION
	==========
	
	To work around this problem, developers writing database applications that
	access a network data store should flush file buffers at any time that
	represents delineation of a transaction; for example, after a bulk operation, or
	prior to closing a file handle, or any time a transaction log is written to.
	This can be done by calling the Win32 FlushFileBuffers API Call.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
