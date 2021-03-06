---
layout: page
title: "Q162514: WINSLI Thunking WinSliCleanup() Closes All Instances"
permalink: /kb/162/Q162514/
---

## Q162514: WINSLI Thunking WinSliCleanup() Closes All Instances

{% raw %}

	Article: Q162514
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetworkkbbuglist
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If two instances of a 16-bit SLI application are opened on a Windows NT system
	using the SNA Server thunking libraries (thunking DLLs installed on Windows NT),
	closing the first instance of the application results in the second instance's
	closing as well.
	
	This problem was observed using the 16-bit Wsli3270.exe included with the SNA
	Serve Software Developer Kit (SDK) (included on the compact disc).
	
	CAUSE
	=====
	
	The 16-bit-to-32-bit SLI thunking interface was not properly handling
	WinSLICleanup from a 16-bit application.
	
	RESOLUTION
	==========
	
	There are two workarounds:
	
	- Run each instance of the 16-bit SLI application in a separate Windows NT
	  virtual MS-DOS machine (VDM).
	
	  or
	
	- Install the 16-bit SNA Server client-server interface on Windows NT. For
	  instructions on how to do this, see the following article in the Microsoft
	  Knowledge Base:
	
	  Q145885 Running 16-bit 3270/FMI Applications on Windows NT & Windows 95
	
	A fix has also been provided; see the fix referenced below.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 2.11, 2.11
	Service Pack 1.
	
	
	A supported fix is now available for 2.11 SP1, but has not been fully
	regression-tested and should be applied only to systems experiencing this
	specific problem. Unless you are severely impacted by this specific problem,
	Microsoft recommends that you wait for the next Service Pack that contains this
	fix. Contact Microsoft Technical Support for more information.
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork kbbuglist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ211 kbSNAServ211SP1
	Version           : WINDOWS:2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
