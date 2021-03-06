---
layout: page
title: "Q180384: HOWTO: Troubleshoot Run-time Error '70' in DCOM Applications"
permalink: /kb/180/Q180384/
---

## Q180384: HOWTO: Troubleshoot Run-time Error '70' in DCOM Applications

{% raw %}

	Article: Q180384
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbDCOM kbRegistry kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 27-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Attempting to access a DCOM Server from a remote client application sometimes
	results in the following error:
	
	  Run-time error '70':
	  Permission Denied
	
	This article describes the most common scenarios in which this error is raised.
	
	MORE INFORMATION
	================
	
	Run-time error '70' is typically the result of a security or permissions issue.
	The following is a list of possible causes of run-time error 70 but is by no
	means a complete or definitive list.
	
	DCOM Is Not Enabled
	-------------------
	
	If the Server machine does not have DCOM enabled, client machines will receive
	run-time error 70 when attempting to access the server. This scenario applies to
	Windows 2000, Windows NT, Windows 95, Windows 98, and Windows Me servers:
	
	1. On the Server machine, run DCOM Config (DCOMCNFG.EXE).
	
	2. Choose the Default Properties tab.
	
	3. Ensure that Enable Distributed COM on this computer is checked. This value is
	  stored in the Windows Registry at the following location:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\OLE
	
	The Client User Does Not Have Sufficient Permissions
	----------------------------------------------------
	
	If the client user does not have the correct permissions, access to the DCOM
	Server can be denied. There are several steps to take in order to ensure your
	client has valid privileges.
	
	If the Server is Windows 95, Windows 98, or Windows Me:
	
	1. Run DCOM Config.
	
	2. Select the DCOM Server application from the list of available applications.
	
	3. Select the Properties button, or double-click the DCOM Server application in
	  the list.
	
	4. Test the server with "Default Access Permissions."
	
	  If run-time error '70' still occurs, the default access permissions are
	  restricting your user. If this is the case, then modify the Default Access
	  Permissions from the Default Security tab in DCOM Config. Grant the client
	  user access permissions.
	
	  If run-time error '70' does not occur running with default access permissions,
	  it is likely that the custom access permissions are restricting your client
	  from accessing the DCOM Server. Choose custom access permissions and select
	  the Edit button. Grant the client user access permissions.
	
	If the Server is Windows NT or Windows 2000:
	
	1. Run DCOM Config.
	
	2. Select the DCOM Server application from the list of available applications.
	
	3. Select the Properties button, or double-click the DCOM Server application in
	  the list.
	
	4. Test the server with "Default Access Permissions," "Default Launch
	  Permissions," and "Custom Configuration Permissions."
	
	  If run-time error '70' still occurs, it is likely that the default access
	  permissions are restricting your user. If this is the case, modify the
	  Default Access Permissions from the Default Security tab in DCOM Config.
	
	  If run-time error '70' does not occur, it is likely that the custom access
	  permissions are restricting your client from accessing the DCOM Server.
	  Choose to use Custom access permissions and choose the Edit button. Grant the
	  client user account access permissions, or grant a group the client user
	  belongs to access permissions.
	
	For more information regarding security groups on Windows NT see the table to
	follow.
	
	There are several group accounts you will find when you configure users and
	groups on Windows NT and Windows 2000. The following list is a summary of who
	belongs to each group:
	
	Group                     Description
	--------------------------------------------------------------------------
	Interactive               Includes all users who log onto a Windows NT or
	                         Windows 2000 system locally (at the console). It 
	                         does not include users who connect to NT
	                         resources across a network or are started as a 
	                         server.
	
	Network                   Includes all users who connect to Windows NT or
	                         Windows 2000 resources across a network. It does 
	                         not include those who connect through an 
	                         interactive logon.
	
	Creator/Owner             The Creator/Owner group is created for each
	                         sharable resource in the Windows NT or
	                         Windows 2000 system. Its membership is the set of 
	                         users who either create a resource (such as a 
	                         file) and who take ownership of them.
	
	Everyone                  All users who access the system, whether locally,
	                         remotely, or across the network.
	
	System                    The local operating system.
	
	The above list includes the group accounts which are intrinsic to Windows NT and
	Windows 2000 systems. Your particular network may include more groups from which
	you may choose. In order to determine the membership of each custom group
	account, you must contact your network administrator.
	
	Attempting to Access DCOM Server Across Non-Trusted Domains
	-----------------------------------------------------------
	
	If your DCOM Server resides in one Windows NT or Windows 2000 domain, and your
	client logs on to a second Windows NT or Windows 2000 domain that is not
	"trusted" by the first, you will receive run-time error '70' when attempting to
	access the DCOM Server.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q158508 : FAQ: COM Security Frequently Asked Questions
	
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q176799 : INFO: Using DCOM Config (DCOMCNFG.EXE) on Windows NT
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDCOM kbRegistry kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : :5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
