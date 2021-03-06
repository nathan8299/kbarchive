---
layout: page
title: "Q160849: INFO: How the SNA Server Client Chooses a &quot;Sponsor&quot; SNA Server"
permalink: /kb/160/Q160849/
---

## Q160849: INFO: How the SNA Server Client Chooses a &quot;Sponsor&quot; SNA Server

{% raw %}

	Article: Q160849
	Product(s): Microsoft SNA Server
	Version(s): 2.11,3.0,4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbtshoot kbusage
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 3.0, 4.0, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When the SNA Server client software initializes (Wnap.exe for Windows 3.x, or
	Snabase.exe for Windows 95, Windows NT and MS-DOS), it opens a "sponsor"
	connection to SnaBase running on an SNA Server in the subdomain. This article
	describes how the SNA client locates a sponsor server.
	
	NOTE: The order that computers running SNA Servers are tried for 3270, LUA or
	LU6.2 sessions is not affected by the sponsor server chosen by the client. For
	information about SNA Server load balancing and hot backup, see the following
	Microsoft Knowledge Base article:
	
	  Q128244 SNA Server Load Balancing and Hot Backup
	
	MORE INFORMATION
	================
	
	The client locates a sponsor server as follows:
	
	- If Named Pipes or TCP/IP is configured on the SNA client, and the client is
	  configured as local to the server(s), the client sends a broadcast to the
	  subdomain and waits for a response from a server-side SnaBase service. The
	  first SnaBase to respond to the client's request will be tried for the
	  sponsor connection.
	
	  NOTE: If the server is located on a different TCP/IP subnet than the client,
	  this broadcast is normally filtered by any intermediate IP routers separating
	  the client and server. In this configuration, the remote connection method
	  should be chosen during SNA client setup.
	
	- If the SNA Server 2.11 Service Pack 1 (or later) client software is being
	  used on Windows 3.x, Windows 95 or Windows NT, the client will randomly
	  choose a server from this list. However, the SNA Windows 3.x and Windows NT
	  clients (and the Windows 95 client, with an update to SNA Server 3.0
	  post-SP1) can be configured to try servers in the order they're configured,
	  by setting the RandomSponsor setting documented below. The MS-DOS client
	  doesn't support TCP/IP sockets. When named pipes is chosen, the MS-DOS client
	  tries the remote servers in order and never randomly chooses the sponsor
	  server.
	
	  NOTE: The SNA client Setup programs only prompt for two remote server names.
	  To configure additional remote servers, they can be manually added for the
	  Windows 3.x, Windows 95 and Windows NT clients as follows:
	
	- Windows 3.x client: Add server names preceded with \\ on the Remote= line in
	  the [WNAP] section of Win.ini, separating the server names with spaces. When
	  connecting over TCP/IP, the server's IP address may be specified explicitly.
	  For example:
	
	  Remote= \\server1 \\server2 \\124.55.69.45
	
	- Windows 95 client: add server names to the following registry value,
	  separated by spaces, but *not* prepended with \\. For example:
	
	  HKEY_LOCAL_MACHINE/Software/Microsoft/SnaBase/Parameters:
	        Sponsors: server1 server2 server3
	
	- Windows NT client: add server names to the following registry value (servers
	  must be listed on separate lines):
	
	  HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services/ 
	     SnaBase/Parameters
	         Sponsors: REG_MULTI_SZ: server1
	                                 server2
	                                 server3
	
	- If NetWare IPX/SPX is configured on the SNA client, and the client is
	  configured as local to the server(s), the client queries the NetWare bindery
	  based on the subdomain name entered during SNA client setup. The server-side
	  SnaBase service automatically registers with the NetWare bindery, specifying
	  the SNA subdomain name and a SAP service type of 0x444. The client retrieves
	  all SNA Server computers from the bindery, and then randomly chooses a
	  server.
	
	- If NetWare IPX/SPX is configured on the SNA Windows 95 or Windows NT client,
	  and the client is configured as remote to the server(s), the client queries
	  the NetWare bindery looking for the specific server names specified during
	  SNA client setup. The server names are stored in the registry as described
	  earlier. The server-side SnaBase service automatically registers with the
	  NetWare bindery and specify their subdomain name and a SAP service type of
	  0x444. The client locates the servers in the bindery, and then randomly
	  chooses a server.
	
	  NOTE: When connecting over Banyan or NetWare IPX/SPX, the SNA Server Windows
	  3.x client only supports local connection mode described earlier.
	
	- If Banyan Vines is configured on the SNA Windows 95 or Windows NT client, the
	  client queries the Banyan StreetTalk directory service based on the
	  StreetTalk list name (that is, subdomain name) entered during SNA client
	  setup. The server-side SnaBase service automatically registers with
	  StreetTalk, creating a StreetTalk List based on the subdomain name, and a
	  PC-based Service for each SNA Server. The client retrieves all SNA Server
	  computers from the StreetTalk List, and then randomly chooses a server.
	
	The sponsor connection must be successfully established before an SNA application
	session (that is, 3270, LUA, APPC, CPIC, CSV, and so forth) will connect to an
	SNA Server.
	
	Background on the Sponsor Connection
	------------------------------------
	
	When the SNA Server client software initializes, it opens a "sponsor" (or
	service) connection to the SnaBase service on an SNA Server in the subdomain.
	The following functions are performed over this sponsor connection:
	
	- The client is notified of SNA Server computers running in the subdomain.
	
	- The server responds to various client requests, including requests for 3270
	  user/group records.
	
	- When connecting over TCP/IP sockets, NetWare IPX/SPX or Banyan Vines, the
	  SnaBase service performs a Windows NT domain log on for the client.
	
	- The client notifies the server of any autostarted invokable TPs that are
	  registered on the client computer. The server sends dynamic load requests to
	  the client when an attach request is received, if the invokable TP is
	  configured on the client.
	
	- The client reports errors to the server, to write to the Windows NT
	  application event log.
	
	The RandomSponsor Setting
	-------------------------
	
	The SNA Server 2.11 Service Pack 1 (or later) client software implements random
	selection of a sponsor server if Named Pipes or TCP/IP is configured with the
	remote option. The initial release of SNA Server 2.11 and previous versions of
	the SNA client software will open remote sponsor servers in the order
	configured.
	
	By randomly choosing a sponsor server, the SNA Windows 3.x, Windows 95 and
	Windows NT clients will tend to load balance across SNA Servers for their
	sponsor connection to help distribute the load across servers.
	
	The RandomSponsor setting can be configured for the Windows 95 client after
	applying SNA Server 3.0 Service Pack 2. If this Service Pack is not applied,
	remote sponsor servers are always tried in random order.
	
	The RandomSponsor setting is enabled by default for Windows 3.x, Windows NT, and
	Windows 95 clients but can be disabled through the following configuration
	setting:
	
	SNA Server Windows 95 Client:
	
	If the SNA Server 3.0 Service Pack 2 Windows 95 client is applied, the following
	entry may be set:
	
	  HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/SnaBase/Parameters/ 
	  RandomSponsor: 0
	
	SNA Server Windows 3.x (or WFW) Client:
	
	In the [WNAP] section of Win.ini:
	
	  RandomSponsor = NO
	
	SNA Server Windows NT Client:
	
	  HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services/SnaBase/Parameters/ 
	  RandomSponsor: REG_DWORD: 0
	
	The client SnaBase service must be restarted to implement this change.
	
	Disabling the RandomSponsor setting causes the SNA client to try the remote
	servers in the order they're configured.
	
	Additional query words: snafaq
	
	======================================================================
	Keywords          : kbnetwork kbtshoot kbusage 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : :2.11,3.0,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
