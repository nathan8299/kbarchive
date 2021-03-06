---
layout: page
title: "Q180866: Persistent Verification Support for APPC Sessions"
permalink: /kb/180/Q180866/
---

## Q180866: Persistent Verification Support for APPC Sessions

{% raw %}

	Article: Q180866
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 02-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	SNA Server 3.0 does not include support for Persistent Verification (PV), a
	method for managing conversation level security on an APPC session. Without PV
	support, a sending LU cannot send a password on the first ATTACH and set the PV
	bit. The PV bit signals the receiving TP to check the security credentials by
	verifying the password.
	
	CAUSE
	=====
	
	Persistent Verification support was not implemented in SNA Server 3.0.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 3.0, 3.0SP1,
	and 3.0SP2.
	
	This problem was corrected in the latest SNA Server version 3.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	PV changes were implemented in SNA Server 4.0 but were not fully retrofitted to
	the SNA Server 3.0 product. In addition, modifications to the APPC interface
	(Wappc32.dll) were needed to provide correct interaction between PV and Already
	Verified (AV) support, which is a second method for managing APPC conversation
	level security. With the hotfix applied, if the host will accept AV and PV, and
	the APPC application specifies "security = AP_SAME", SNA Server does the
	following:
	
	1. If it does not detect that the user is signed on to the host, it sends an
	  ATTACH with the AV bit set and the PV bits set to "sign-on requested". A
	  password is not included.
	
	2. If it does detect that the user is signed on, it sends an ATTACH with the AV
	  bit set and the PV bits set to "already signed on". Again, a password is not
	  included.
	
	The most basic way to keep an APPC conversation secure is to send a user_id and
	password on each ATTACH, which can then be verified by the receiving LU. The
	problem with this is that the password is continuously passed in messages,
	increasing the likelihood of its being intercepted. PV and AV both provide a
	mechanism for reducing (or removing altogether) the number of messages that
	contain the password, and thereby improving security.
	
	For AV the password is never sent on any ATTACH. The receiving LU trusts the
	sending LU to have done all of the security checking. If a receiving LU trusts a
	sending LU, the sending LU can avoid including the password on any ATTACH by
	setting the AV indicator bit instead. The AV bit tells the receiving LU that the
	sending LU has already verified the TP's credentials (by some private method)
	and the receiving LU does not have to worry about doing any checking itself.
	
	For PV, the password is sent on the first ATTACH, and is never sent again. On the
	first ATTACH, the PV bit is set, and a password is included. This signals the
	receiving LU to check the password and then add the user_id to a list of users
	who do not need to be verified again. On the second and subsequent ATTACHes the
	PV bit is set, but no password is included. This signals the receiving TP that
	it just needs to check that the user is in the list of users it has verified in
	the past.
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
