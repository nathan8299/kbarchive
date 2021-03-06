---
layout: page
title: "Q308439: IIS Admin Service Fails to Start When the Metabase Is Too Large"
permalink: /kb/308/Q308439/
---

## Q308439: IIS Admin Service Fails to Start When the Metabase Is Too Large

{% raw %}

	Article: Q308439
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbCOMIS kbWin2000sp3fix
	Last Modified: 15-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the metabase is too large to complete the initialization in the Service
	Control Manager timeout window, you cannot start the IIS Admin Service.
	
	CAUSE
	=====
	
	When you start the service, the Service Control Manager is notified that the
	service is going to start in a certain number of seconds or less. This time is
	hard-coded in the IIS Admin Service to 10,000 milliseconds, which may not be
	enough time if the metabase is large.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows 2000. For
	additional information, click the following article number to view the article
	in the Microsoft Knowledge Base:
	
	  Q260910 How to Obtain the Latest Windows 2000 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	+---------------------------------------------------------------------+
	| Name         | Size    | Date        | Time  | Version   | Platform | 
	+---------------------------------------------------------------------+
	| Aqueue.dll   | 321,296 | Nov-13-2001 | 00:37 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Asp.dll      | 333,072 | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Fscfg.dll    | 299,792 | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Ftpctrs2.dll | 8,464   | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Ftpmib.dll   | 6,416   | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Httpmib.dll  | 9,488   | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Iisadmin.dll | 16,656  | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Infoadmn.dll | 13,584  | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Infocomm.dll | 246,032 | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Isatq.dll    | 62,736  | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Mailmsg.dll  | 66,832  | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Ntfsdrv.dll  | 38,160  | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| Smtpsvc.dll  | 435,984 | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	| W3ctrs.dll   | 7,440   | Nov-13-2001 | 00:49 | 5.00.0984 | x86      | 
	+---------------------------------------------------------------------+
	
	
	WORKAROUND
	==========
	
	To work around this problem, reduce the size of the metabase.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Windows 2000 Service Pack 3.
	
	MORE INFORMATION
	================
	
	This fix is implemented by adding two registry values. One allows you to modify
	the time for the service to start, and one allows you to modify the time for the
	service to stop.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Iisadmin\Parameters
	
	3. On the Edit menu, click Add Value, and then add the following registry value:
	
	  Value Name: WaitHintStart
	  Data Type: REG_DWORD
	  Value: <Time to wait for service to start (in milliseconds)>
	
	  Value Name: WaitHintStop
	  Data Type: REG_DWORD
	  Value: <Time to wait for service to stop (in milliseconds)>
	
	4. Quit Registry Editor.
	
	To estimate the numbers that you should enter for the value, follow these steps:
	
	1. Add the previous registry values, then change the value to a large number.
	
	2. Start the service and note how long it takes to start.
	
	3. Modify the numbers according to the amount of time that you think the service
	  will take to start. Overestimate the time, because if the service ever takes
	  longer than the allotted time to start, the W3SVC service and any other
	  dependent services will not start.
	
	Additional query words: kbIISCom iis 5
	
	======================================================================
	Keywords          : kbCOMIS kbWin2000sp3fix 
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
