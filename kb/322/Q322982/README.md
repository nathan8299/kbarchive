---
layout: page
title: "Q322982: Windows NT 4.0 DFS Stops Working After You Apply Post-SP6a SRP"
permalink: /kb/322/Q322982/
---

## Q322982: Windows NT 4.0 DFS Stops Working After You Apply Post-SP6a SRP

{% raw %}

	Article: Q322982
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 17-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you apply the Windows NT 4.0 Post-Service Pack 6a (SP6a) Security Rollup
	Package (SRP) on a Windows NT 4.0-based server, Windows 95-based clients that
	have the Windows 95 DFS client software installed cannot connect to Distributed
	File System (DFS) shares. When this issue occurs, the user on the Windows
	95-based client receives the following error message:
	
	  This folder was moved or removed.
	
	For additional information about the SRP, click the article number below to view
	the article in the Microsoft Knowledge Base:
	
	  Q299444 Post-Windows NT 4.0 Service Pack 6a Security Rollup Package (SRP)
	
	RESOLUTION
	==========
	
	To try to resolve this issue, apply the hotfix that is mentioned in the
	following Microsoft Knowledge Base article:
	
	  Q248740 Upgrading to Windows NT 4.0 SP5 Causes Stop 0x50 in DFS
	  DosPathName.Length
	
	Apply this hotfix on the Windows NT 4.0-based DFS server. This hotfix is not
	directly related to the problem, but the hotfix includes an updated Dfs.sys
	driver that might resolve the issue.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWin95search kbZNotKeyword3
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
