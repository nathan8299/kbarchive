---
layout: page
title: "Q185618: Schannel.dll and Schnl128.dll Updates in Windows NT 4.0 SP4"
permalink: /kb/185/Q185618/
---

## Q185618: Schannel.dll and Schnl128.dll Updates in Windows NT 4.0 SP4

{% raw %}

	Article: Q185618
	Product(s): Internet Information Server
	Version(s): WINNT:4.0
	Operating System(s): 
	Keyword(s): kbFEA kbWinNT400sp4fea
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The new Schannel.dll and Schnl128.dll files in Windows NT 4.0 Service Pack 4
	have been modified to address the issues listed below.
	
	MORE INFORMATION
	================
	
	The changes made to the above listed files include:
	
	- Cache access has been unserialized to improve performance on the server side.
	
	- The cache automatically grows itself, for improved memory usage. (the server
	  had been blocking connections under heavy load).
	
	- DES, 3DES, and DHE ciphers have been added (for compatibility with other
	  implementations).
	
	- Fortezza has been added (a government cipher).
	
	- New APIs were added to the SSPI interface.
	
	- RPC fixes were made. Some bugs were fixed, allowing connection mode usage of
	  schannel.
	
	To obtain the latest service pack for Windows NT version 4.0, please see the
	following article in the Microsoft Knowledge Base.
	
	  Q152734 : How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	======================================================================
	Keywords          : kbFEA kbWinNT400sp4fea 
	Technology        : kbiisSearch kbiis400
	Version           : WINNT:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
