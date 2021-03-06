---
layout: page
title: "Q131404: Err Msg: Cannot Find the File RNETWORK.GLB on the Server"
permalink: /kb/131/Q131404/
---

## Q131404: Err Msg: Cannot Find the File RNETWORK.GLB on the Server

{% raw %}

	Article: Q131404
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are downloading the post office address book, you receive the following
	error message:
	
	  Cannot find the file RNETWORK.GLB on the Server
	
	CAUSE
	=====
	
	The RNETWORK.GLB file is either missing or damaged when you try to download it
	from a Microsoft Mail 3.x post office. This error message does not occur when
	you try to download an address book from a Windows for Workgroups or Windows 95
	post office.
	
	RESOLUTION
	==========
	
	The Microsoft Mail administrator should run the ADMIN.EXE tool to set up a
	remote user and run Regenerate. This creates the RNETWORK.GLB file. For more
	information, please consult your Microsoft Mail documentation.
	
	MORE INFORMATION
	================
	
	Microsoft Exchange in Windows 95 requires that the RNETWORK.GLB file be present
	to download the address book, as does the Microsoft Mail remote client.
	
	RNETWORK.GLB is a file containing the global address list. This is a list
	containing all the users from all the post offices on the network. The list does
	not contain external post office addresses (such as those using gateway
	addressing).
	
	When the RNETWORK.GLB file is present at the post office, Windows 95 sets up a
	mini post office in the MSREMOTE.SFS subdirectory for the downloaded copy of the
	post office list. After downloading the RNETWORK.GLB file, Microsoft Exchange
	explodes the file into the MSREMOTE.SFS directory, creating the local copy of
	the post office list. This list needs to be updated periodically.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWin95search kbZNotKeyword3
	
	=============================================================================
	

{% endraw %}
