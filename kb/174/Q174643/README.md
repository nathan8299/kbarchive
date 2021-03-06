---
layout: page
title: "Q174643: SNA Server RUI Application Unable To Send NSPE +RSP"
permalink: /kb/174/Q174643/
---

## Q174643: SNA Server RUI Application Unable To Send NSPE +RSP

{% raw %}

	Article: Q174643
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1
	Operating System(s): 
	Keyword(s): kbnetwork kbprogrammingkbbuglist
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If an RUI application receives a NSPE request (NS Procedure Error) from the host
	and submits a positive response, the SNA Server never sends the NSPE +RSP to the
	host. This problem was initially reported by an application developer writing to
	the SNA Server Win32 LUA RUI programming interface. When this problem occurs, no
	events are generated and there are no other problems encountered, except that
	the host does not receive a NSPE +RSP on the SSCP-LU session.
	
	CAUSE
	=====
	
	SNA Server did not support sending responses to Network Services (NS) RUs via
	the RUI library. NS RU responses each require a 3-byte NS Header, though the RUI
	library only accomodated a 1-byte command.
	
	RESOLUTION
	==========
	
	The SNA Server RUI interface has been enhanced to support 3-byte response RU's
	if the following conditions are met:
	
	- the response is on the LU-SSCP session
	
	- the FI bit is set in the RH
	
	- the RU category is FMD
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 2.11, 2.11
	SP1, 2.11 SP2, 3.0, and 3.0 SP1. This problem has been corrected in SNA Server
	3.0 SP2. For information on obtaining the Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork kbprogramming kbbuglist
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
