---
layout: page
title: "Q273639: HOW TO: Start IISAdmin and Dependent Services Under a Debugger"
permalink: /kb/273/Q273639/
---

## Q273639: HOW TO: Start IISAdmin and Dependent Services Under a Debugger

{% raw %}

	Article: Q273639
	Product(s): Internet Information Server
	Version(s): 3.0,4.0,5.0
	Operating System(s): 
	Keyword(s): kbHOWTOmaster
	Last Modified: 22-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Server versions 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Set Service Options
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This step-by-step article describes how to start a service (specifically
	IISAdmin and its dependent services) under a debugger.
	
	Occasionally, issues occur when you start the IISAdmin service or one of its
	dependent services, such as the World Wide Web Publishing service or the FTP
	Publishing service. These services may stop responding (hang) or quit (crash) in
	a way that is not caught by the default system debugger. Also, if a service
	experiences a problem when it starts, the Service Control Manager (SCM)
	gracefully stops the service and reports to the Event Log that there was a
	problem starting the service. If this information is not enough, you must
	determine where the issue lies during startup. If you are debugging an
	executable file, you can start the debugger of your choice, and then run the
	executable file under the debugger. This becomes more difficult when the
	executable file in question is running as a Microsoft Windows NT service.
	Although the environment is a little different, the approach is very similar.
	
	This article describes how to start a service (specifically IISAdmin and its
	dependent services) under a debugger. The debugger that is used in the example
	is WinDBG. To download and install the debugging tools, visit the following
	Microsoft Web site:
	
	  Microsoft Debugging Tools
	  http://www.microsoft.com/ddk/debugging/
	
	Set Service Options
	-------------------
	
	1. Set the Image File Execution options so that when the service (or the
	  executable file) starts, it starts under the debugger. Because you are
	  dealing directly with a Windows NT service, make sure that you turn on the
	  Interact With the Desktop option in the Log On As section of the Service
	  Properties dialog box. Otherwise, when the service starts, it loads in the
	  debugger, and you will not see it.
	
	  REGEDIT4
	
	  [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\inetinfo.exe]
	  "Debugger"="C:\\Debuggers\\windbg -g"
	
	NOTE: The path that points to the debugger (WinDbg in the examples) cannot
	contain any spaces, nor can you use extensions in the debugger path; for
	example, it must be windbg, and not windbg.exe.
	
	2. To debug IIS, including the File Transfer Protocol (FTP), Simple Mail
	  Transfer Protocol (SMTP), Network News Transfer Protocol (NNTP), Web, and
	  other services that run under the Inetinfo.exe process, set the IISAdmin
	  service to Interact with the Desktop.
	
	3. At a command prompt, issue a net stop iisadmin /y command to stop IISAdmin
	  and all the dependent services, and then issue a net start w3svc command to
	  start the World Wide Web Publishing service and the IISAdmin service.
	
	4. Start any other related services. This last step may be omitted or changed
	  based on the situation. For example, if you are debugging an FTP (MSFTPSVC)
	  service startup issue, instead of starting the World Wide Web Publishing
	  service, you only have to start the FTP Publishing service (net start
	  msftpsvc).
	
	5. When the debugger is running, you can set up various options, such as symbol
	  path. From this point, you can debug the service as any other executable
	  process.
	
	REFERENCES
	==========
	
	For additional information about debugging, click the article numbers below to
	view the articles in the Microsoft Knowledge Base:
	
	  Q286350 HOWTO: Use Autodump+ to Troubleshoot Hangs and Crashes
	
	  Q261871 INFO: COM+ and MTS Debugging Resources
	
	  Q183480 HOW TO: Debug ISAPI DLLs Under IIS 4.0 and IIS 5.0
	
	  Q238788 How to Debug CGI Applications Running Under IIS
	
	
	For additional information about debugging a Windows NT service, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q170738 Debugging a Windows NT Service
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHOWTOmaster 
	Technology        : kbiisSearch kbiis500 kbiis400 kbiis300
	Version           : :3.0,4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
