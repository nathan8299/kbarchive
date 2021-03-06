---
layout: page
title: "Q195399: SNA Print Service Access Violation in S3pcsctl()"
permalink: /kb/195/Q195399/
---

## Q195399: SNA Print Service Access Violation in S3pcsctl()

{% raw %}

	Article: Q195399
	Product(s): Microsoft SNA Server
	Version(s): 3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The SNA Print service (Snaprint.exe) may fail unexpectedly with an access
	violation, causing all print sessions to end abnormally. When this specific
	problem occurs, SNA Server will log the following event, along with an
	indication of a failure in routine "s3pcsctl":
	
	  Source: SNA Server
	  Event: 624
	  Creating dump file SNADUMP.LOG for snaprint.exe
	
	If Drwtsn32.exe is the default debugger, the Drwtsn32.log file will indicate an
	access violation fault in routine "s3pcsctl()". The log entry will appear as
	follows:
	
	  Application exception occurred:
	
	  App: exe\snaprint.dbg (<pid>) <date, time omitted > Exception
	  number: c0000005 (access violation)
	
	  [...]
	
	  State Dump for Thread Id 0x40
	
	  eax=02020380 ebx=000af710 ecx=00000018 edx=6020ecdc esi=000af710
	  edi=40404040
	  eip=60d838ab esp=0c20ff68 ebp=00000008 iopl=0
	  nv up ei pl nz na pe nc
	  cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000 efl=00000202
	
	  function: s3pcsctl
	
	  60d8388a 55 push ebp 60d8388b 57 push edi 60d8388c 68b811da60 push 0x60da11b8
	  60d83891 6a00 push 0x0 60d83893 e8b8dfffff call PreAsyncTrace (60d81850)
	  60d83898 83c414 add esp,0x14 60d8389b 8b150011d860 mov
	  edx,[_imp____dwEnabledTraces
	
	  (60d8110
	
	  60d838a1 8d4c6d00 lea ecx,[ebp+ebp*2] 60d838a5 8d044f lea eax,[edi+ecx*2]
	  60d838a8 c1e003 shl eax,0x3
	
	  FAULT ->60d838ab 8b988411d860     mov     ebx,[eax+0x60d81184]
	
	  *----> Stack Back Trace <----*
	
	  FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	  00000008 00000000 00000000 00000000 00000000 00000000 ppd3270!s3pcsctl
	
	CAUSE
	=====
	
	The print server is mishandling long streams of NULL characters or spaces in the
	print job when "No Line Formatting" is selected for the print session.
	
	
	RESOLUTION
	==========
	
	SNA Server 3.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	3.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q184307 How to Obtain the Latest SNA Server Version 3.0 Service Pack
	
	
	
	SNA Server 4.0
	--------------
	
	This problem was corrected in the latest SNA Server version 4.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	WORKAROUND
	==========
	
	Try clearing the "No Line Formatting" check box within the SNA print session
	3270 Configuration tab.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 3.0, 3.0
	Service Pack 1, 3.0 Service Pack 2, 3.0 Service Pack 3, 4.0, and 4.0 Service
	Pack 1. This problem was first corrected in SNA Server 3.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	For more information about the "No Line Formatting" option, see the following
	Knowledge Base article:
	
	  ARTICLE-ID: Q178514
	  TITLE     : "No Line Formatting" Option isn't Explained in SNA Server                Help
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : :3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
