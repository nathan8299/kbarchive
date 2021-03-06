---
layout: page
title: "Q222641: XCON: Content Conversion Error Sending Contact as an Attachment"
permalink: /kb/222/Q222641/
---

## Q222641: XCON: Content Conversion Error Sending Contact as an Attachment

{% raw %}

	Article: Q222641
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 EXC55SP3Fix
	Last Modified: 30-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you send an Outlook Contact as an Attachment over an X.400 Connector, a
	Content Conversion error may occur. The sender of the message may get a
	non-deliver report (NDR) similar to the following:
	
	  Your message did not reach some or all of the intended recipients.
	  Subject: test
	  Sent: 10.02.99 16:48
	
	  The following recipient(s) could not be reached:
	  Testuser on 10.02.99 16:48
	
	  A syntax error was detected in the content of the message
	  The MTS-ID of the original message is:
	  c=DE;a=admd;p=prmd;l=SERVER1-990210154808Z-1
	  MSEXCH:MSExchangeMTA:Organization:SERVER1
	
	The following may be logged in the Windows NT Server Application Event log:
	
	  Event ID: 210
	  Source: MSExchangeMTA
	  Type: Warning
	  Category: X.400 Service
	  Description: An internal MTA Error occurred. Content Conversion for message
	  c=DE;a=admd;p=prmd;l=SERVER1-990210154808Z-1 failed. Conversion Failure 4108
	  Original Content Type: 2A864886F7140501, New Content Type: 56010A00.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Message Transfer Agent (MTA)
	
	+---------------------------+
	| File name    | Version    | 
	+---------------------------+
	| Dbserver.sch | N/A        | 
	+---------------------------+
	| Dcprods.cat  | N/A        | 
	+---------------------------+
	| Ems_rid.dll  | 5.5.2574.0 | 
	+---------------------------+
	| Emsmta.exe   | 5.5.2574.0 | 
	+---------------------------+
	| Info4log.cfg | N/A        | 
	+---------------------------+
	| Infoblog.cfg | N/A        | 
	+---------------------------+
	| Infodlog.cfg | N/A        | 
	+---------------------------+
	| Infollog.cfg | N/A        | 
	+---------------------------+
	| Infotlog.cfg | N/A        | 
	+---------------------------+
	| Mtacheck.exe | 5.5.2574.0 | 
	+---------------------------+
	| Mtamsg.dll   | 5.5.2574.0 | 
	+---------------------------+
	| P2.xv2       | N/A        | 
	+---------------------------+
	| X400om.dll   | 5.5.2574.0 | 
	+---------------------------+
	| X400om.dll   | 5.5.2574.0 | 
	+---------------------------+
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 3.
	
	
	Additional query words: word-wrap truncated deleted
	
	======================================================================
	Keywords          : exc55 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
