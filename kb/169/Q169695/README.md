---
layout: page
title: "Q169695: XCON: Invalid Originator Address When Sending to X.400"
permalink: /kb/169/Q169695/
---

## Q169695: XCON: Invalid Originator Address When Sending to X.400

{% raw %}

	Article: Q169695
	Product(s): Microsoft Exchange
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 13-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you send a message from Microsoft Mail through Microsoft Exchange Server
	4.0 to an address on an X.400 messaging system, a reply to this message may not
	be possible. This occurs if you (the Microsoft Mail user) are not a Custom
	Recipient on the Microsoft Exchange Server, which can happen if, for example,
	directory synchronization is not yet finished.
	
	CAUSE
	=====
	
	The message will arrive at the remote X.400 system with an invalid X.400
	originator address in the message header fields. The X.400 address will only
	contain a DDA Type and a DDA Value, which contains the Microsoft Mail Address.
	For example:
	
	  DDA Type=MS;DDA Value=Net/PO/User
	
	This address is invalid because mandatory parts are missing. A valid address
	looks like this:
	
	  C=Country;A=Admin;P=Private;O=Org;DDA Type=MS;DDA Value=Net/PO/User
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 4.0. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 4.0. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : 4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
