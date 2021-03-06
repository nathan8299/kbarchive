---
layout: page
title: "Q102016: Mac Srv: User Names Listed in Italics in Address List"
permalink: /kb/102/Q102016/
---

## Q102016: Mac Srv: User Names Listed in Italics in Address List

{% raw %}

	Article: Q102016
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:3.0,3.1,3.1a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, versions 3.0, 3.1, 3.1a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In versions 3.0 and later of Microsoft Mail for AppleTalk Networks, the user
	names in the mail addressing screen may be displayed in an italic font.
	
	CAUSE
	=====
	
	This display serves as a warning to both users and Network Managers that the
	remote server is not communicating with the local server. This can occur for the
	following reasons:
	
	- The AppleTalk network connection has been broken between the servers. The
	  names will be displayed in italics if one half the amount of time set in the
	  "Remove Users not seen in X days" Server Setting has passed.
	
	- Site names were recently implemented, but message routing has not yet been
	  configured.
	
	RESOLUTION
	==========
	
	If you want to remove the italicized user names from the server, you do not need
	to do anything; the user list will be removed when the specified duration
	expires. To speed up this process, the Network Manager can use the Admin-Remove
	User Lists command (from the Admin menu, choose Remove User Lists) from within
	the Mail Network Administrator program.
	
	If you do not want to remove the names, follow the troubleshooting procedure
	below to re-establish communication with the remove server.
	
	To force the servers to exchange/update user lists
	--------------------------------------------------
	
	1. From the Mail Network Administrator program, choose the Global Server report,
	  and then check the last time the remote server was available.
	
	  The remote server should have been available at some point less than six hours
	  ago. If more than six hours has passed, the problem may be network related.
	
	2. From the Microsoft Mail workstation program on the local server, use the
	  Chooser to locate the name of the remote server.
	
	  If the remote server name is not listed in the Chooser, there is a network
	  problem.
	
	3. From the Administrator program on both servers, run a Global Routing report.
	
	  If you do not use message routing, ensure the site name is identical for both
	  servers, that routing has been not enabled for both servers, and that no
	  errors appear in the Global Routing report.
	
	  If you use message routing, ensure that the Global Routing report correctly
	  reports the bridge between the servers and that no errors appear.
	
	4. If routing has been enabled, from the Network Administrator program on both
	  servers, choose the Admin-Configure Routing command.
	
	  Make sure both the Import and Export options are enabled.
	
	5. For Microsoft Mail version 3.1 and later servers, choose the Scan Network Now
	  command from the Network Administrator program. For Microsoft Mail version
	  3.0 servers, restart the server.
	
	6. If, after a reasonable period of time, the servers do not exchange user
	  lists, add a temporary user name to the remote server. This will force the
	  server to send an updated user list.
	
	7. If the servers still do not exchange user lists, choose the Remove User List
	  command from the Network Administrator program to remove the troubled
	  server.
	
	  NOTE: When you remove a user list, you also remove all resources on the server
	  that pertain to the remote server. You will need to revise groups and
	  personal address lists that contained user names from the removed user list.
	
	MORE INFORMATION
	================
	
	Microsoft Mail servers automatically scan the AppleTalk network, seeking other
	servers that have been set up to exchange user lists and user messages. If a
	remote server becomes unavailable after exchanging user lists, the current
	server begins the countdown to remove the user list it obtained from the remote
	server. The time for removing remote user lists is specified in the Server
	Settings option, which you can access from the Mail menu of the workstation
	while you are signed in to Microsoft Mail as the network administrator.
	
	When one-half of the time in the Remove User List option expires, the current
	server begins displaying in italics all user names from the unavailable remote
	server. For example, the default setting for removing user lists is seven days;
	when three and one-half days have passed since the last time the Remote server
	was available, user names from the Remote server begin to appear in italics.
	
	When all of the time specified in the Remove User List option expires, the
	italicized user names and all server resources regarding the remote server are
	removed from the local server.
	
	Additional query words: 3.00 3.10 3.10a
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN300 kbMailATN310 kbMailATN310a
	Version           : WINDOWS:3.0,3.1,3.1a
	
	=============================================================================
	

{% endraw %}
