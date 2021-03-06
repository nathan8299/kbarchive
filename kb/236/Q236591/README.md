---
layout: page
title: "Q236591: SNA Server LU Allocation Favors Active Remote Connections"
permalink: /kb/236/Q236591/
---

## Q236591: SNA Server LU Allocation Favors Active Remote Connections

{% raw %}

	Article: Q236591
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0,4.0 SP1,4.0 SP2
	Operating System(s): 
	Keyword(s): kbsna400sp3fea kbFEA sna4 kbsna400sp1 kbsna400sp2
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1, 4.0 SP2 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	In the following scenario, two SNA Servers are deployed, SNAS1 (primary) and
	SNAS2 (backup). SNAS1 is geographically local to the client and SNAS2 is
	geographically remote from the client. Both SNA Servers share the same domain
	and organization-wide TN3270 LU pool.
	
	The PU on SNAS1 undergoes a scheduled or unscheduled recycle and recovers to
	return to an active/available status. During this period of downtime, a new
	client request for a session is serviced by SNAS2, and thereafter, the following
	behavior may be observed:
	
	- If a new user connects to an LU in the pool through SNAS1, they are actually
	  given an LU from SNAS2.
	
	- After all pool LUs are consumed on SNAS2, only then will SNAS1 allocate its
	  own LUs that are in the pool.
	
	- If a previously "In-Use" LU on SNAS2 is released and becomes available, a new
	  user connecting to SNAS1 will be given this remote LU rather than SNAS1
	  allocating one of its local LU resources.
	
	Although this behavior is by design, there have been requests to support an
	option for TN3270 that allocates sessions across restarted/recovered local
	connections in preference to remote connections.
	
	NOTE: This feature does not provide TN3270 client load balancing across more than
	one TN3270 server. That function must be provided by the TN3270 client or
	possibly the TCP/IP name service being used. If this functionality is needed,
	SNA Server provides transparent client load balancing across SNA Server
	computers using its native 3270 interface. For additional information about SNA
	Server load balancing, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q185446 TN3270 Server LUA Pool Use Should Load Balance Across Servers
	
	  Q128244 SNA Server Load Balancing and Hot Backup
	
	For additional information about shared LUA pool use by more than one TN3270
	server, please see the following article in the Microsoft Knowledge Base:
	
	  Q182139 LUA Pool Cannot Be Assigned to Two TN3270 Servers
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	After this update is applied to the SNA Server, this new behavior for TN3270
	(LUA/3270 application) resource location is enabled by setting the ResLocFlags
	registry entry to a DataValue of either 0x8000 or 0x8001 under:
	
	  KEY_LOCAL_MACHINE\System\CurrentControlSet\Services \TN3270\Parameters
	  ResLocFlags: REG_DWORD,default = 0
	
	If the DataValue is 0x8000, then all Open(SSCP) messages are first sent to the
	local SNA Server even if an existing connection is open to a remote server.
	
	If the DataValue is 0x8001, it enables both the "try local first" and the "load
	balance amongst remote servers" feature as detailed in article Q185446.
	
	In both cases, the SNA Server first tries to use local resources; if a request
	cannot be satisfied locally, it uses a remote resource. There is no load
	balancing among local SNA Servers, that is, the TN3270 Server first consumes all
	resources from one local SNA server before allocating resources from the other
	local SNA servers.
	
	NOTE: The default behavior is to always use an existing active connection first.
	
	After this update is applied and the ResLocFlags entry is set, the SnaBase
	service and TN3270 service must be restarted for the change to take effect.
	
	MORE INFORMATION
	================
	
	This feature is available in the latest service pack for SNA Server version 4.0.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	This feature was first included in SNA Server version 4.0 Service Pack 3.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna400sp3fea kbFEA sna4 kbsna400sp1 kbsna400sp2 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400 kbSNAServ400SP1 kbSNAServ400SP2
	Version           : WINDOWS:4.0,4.0 SP1,4.0 SP2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
