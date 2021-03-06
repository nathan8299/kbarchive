---
layout: page
title: "Q230285: XADM:&quot;Denial of service&quot; Vulnerability in Store with IMAP"
permalink: /kb/230/Q230285/
---

## Q230285: XADM:&quot;Denial of service&quot; Vulnerability in Store with IMAP

{% raw %}

	Article: Q230285
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): kbFEA exc55 EXC55SP3Feakbbuglist kbfixlist
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server information store process may become unresponsive
	to clients and the Exchange Administrator program. Windows NT may report within
	a dialog box that the system is running low on virtual memory. Additionally, the
	desktop user interface may become sluggish, and over time, computer performance
	may degrade to the point of malfunction, requiring a restart.
	
	The overall information store CPU usage in Performance Monitor will appear
	relatively high. Also, the information store's "per thread processor
	utilization" reveals that only a few threads (~3) appear active within the
	information store, but that these threads cycle through periods of high CPU
	usage.
	
	These symptoms may ensue after restarting the information store service.
	
	CAUSE
	=====
	
	The IMAP protocol, documented in RFC2060 (and predecessors), states that a
	subset of IMAP commands are valid for a connection even in the "unauthenticated"
	state, requiring that the IMAP server respond to such client command requests
	even when the client is without a valid log on. IMAP clients or applications may
	malfunction (or attack) by incessantly sending [full] TCP frames containing of
	one or more valid IMAP commands. The Exchange Server information store was not
	protecting itself from such a malfunction (or attack).
	
	RESOLUTION
	==========
	
	A feature is now available that allows the information store to protect itself
	from such a malfunction. This feature is available in the latest service pack
	for Exchange Server version 5.5. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this feature should have the following file attributes or
	later:
	
	Components: Information Store and Directory
	
	+--------------------------+
	| File name   | Version    | 
	+--------------------------+
	| Store.exe   | 5.5.2600.0 | 
	+--------------------------+
	| Mdbmsg.dll  | 5.5.2600.0 | 
	+--------------------------+
	| Gapi32.dll  | 5.5.2600.0 | 
	+--------------------------+
	| Netif.dll   | 5.5.2600.0 | 
	+--------------------------+
	| Dsamain.exe | 5.5.2600.0 | 
	+--------------------------+
	
	This feature was first included in Exchange Server 5.5 Service Pack 3.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5.
	
	MORE INFORMATION
	================
	
	In this case, a network trace was taken on the Exchange Server segment. In
	viewing the trace, it could be seen that three other nodes were responsible for
	roughly 85 percent of the traffic to and from the Exchange Server computer, and
	that this traffic was coming in and out of the IMAP port, port 143. Filtering
	the traffic between one of these nodes and the Exchange Server computer revealed
	that the node was incessantly sending packed TCP frames full of "no operation"
	(NOOP) commands. NOOPs are one of the IMAP commands that are valid even in the
	unauthenticated state. However, it is unreasonable and unnecessary to submit
	packed 1,500-byte TCP frames full of them. The Exchange Server computer was
	attempting to queue and respond to each and every command. After the
	hotfix-feature is installed, the server will check the queue of commands
	pending, and if over 100, will issue a TCP reset to disconnect the client.
	
	
	Generating a Performance Monitor log that includes the Memory and Process objects
	will record the history of memory resource consumption on the Exchange Server
	computer. For this case, when viewing the data in the log, the Process:Virtual
	bytes counter for the Store and Services processes will be seen to rise rapidly
	until all virtual memory is exhausted.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbFEA exc55 EXC55SP3Fea kbbuglist kbfixlist
	Component         : IMAP4
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
