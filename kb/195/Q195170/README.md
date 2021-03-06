---
layout: page
title: "Q195170: SNA Server Sends an Incorrect Sequence Number in BIND Response"
permalink: /kb/195/Q195170/
---

## Q195170: SNA Server Sends an Incorrect Sequence Number in BIND Response

{% raw %}

	Article: Q195170
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
	
	A previously functioning logical unit (LU) may remain pending even if no one
	else is using it at the moment. On the host, this LU is shown as active.
	
	CAUSE
	=====
	
	If an SNA Server sends an OPEN PLU Request to an application, it may send a BIND
	-RSP with an incorrect sequence number to the host if it receives a lost
	locality from the dynamic address module (DMOD) indicating that the application
	has unexpectedly terminated, or that the network connection to the client
	running the application has been lost.
	
	The host ignores this response and keeps the LU active, waiting for the correct
	BIND response and thus preventing this LU from being used.
	
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
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version
	3.0, 3.0 Service Pack 1, 3.0 Service Pack 2, 3.0 Service Pack 3, 4.0, and 4.0
	Service Pack 1. This problem was first corrected in SNA Server 3.0 Service Pack
	4.
	
	MORE INFORMATION
	================
	
	If SNA Server Data Link Control (DLC) and 3270 message tracing is enabled, the
	resulting trace may appear as follows:
	
	A BIND request arrives from the host:
	
	     DLC   ------------------------------------------------------------------
	     ---
	     DLC   04160080->01020401 DLC DATA
	     DLC                      DAF:02 OAF:01 ODAI:off Exp.
	     DLC                      BIND   RQD SC  FI BC EC DR1
	     DLC
	     DLC   ---- Header  at address 0145965C, 1 elements ----
	     DLC   04000004 10112D00 02019586 0100EB00     <......-...nf....>
	     DLC
	     DLC   ---- Element at address 0197322C, start 10, end 58 ----
	     DLC   6B800031 010303B1 90308000 05858785     <k..1.....0...ege>
	     DLC   00028000 00000018 5018507F 000007C1     <........P.P<7F>...A>
	     DLC   D5F6F3D5 D4E30000 08E3E4F6 F3C7F3F0     <N63NMT...TU63G30>
	     DLC   F0                                      <0               >
	
	The Node (SNA Server service) sends an OPEN PLU to the application:
	
	     FMI   -------------------------------------------------------
	     FMI   01022E06->A9120000 OPEN  PLU  REQUEST
	     FMI                      FMI  CredR:5 CredS:1
	     FMI
	     FMI   ---- Header  at address 0145FFC8, 2 elements ----
	     FMI   01020202 01000005 00010000 0100EB00     <................>
	     FMI
	     FMI   ---- Element at address 0196206C, start 1, end 28 ----
	     FMI   0B001154 55363347 33304C55 412D5255     <...TU63G30LUA-RU>
	     FMI   49202020 00050100 04000000              <I   ........    >
	     FMI
	     FMI   ---- Element at address 0197322C, start 4, end 58 ----
	     FMI   2D000201 95866B80 00310103 03B19030     <-...nfk..1.....0>
	     FMI   80000585 87850002 80000000 00185018     <...ege........P.>
	     FMI   507F0000 07C1D5F6 F3D5D4E3 000008E3     <P<7F>...AN63NMT...T>
	     FMI   E4F6F3C7 F3F0F0                         <U63G300         >
	
	In this situation, the application connection was broken, or the application
	itself was ended for some reason. This results in a Lost Locality to the SNA
	Server's Node.
	
	Because SNA Server knows that a BIND RSP is outstanding, it must generate and
	send a -VE BIND RSP to the host.
	
	     DLC   ------------------------------------------------------------------
	     ---
	     DLC   01020401->04160080 DLC DATA
	     DLC                      DAF:01 OAF:02 ODAI:off Exp.
	     DLC                      BIND   -RSP SC  FI SD BC EC DR1
	     DLC
	     DLC   ---- Header  at address 01460064, 1 elements ----
	     DLC   00000000 00002D00 010211FC 01000200     <......-.........>
	     DLC
	     DLC   ---- Element at address 01958794, start 10, end 17 ----
	     DLC   EF900008 45000031                       <....E..1        >
	     DLC   ------------------------------------------------------------------
	     ---
	
	But instead of sending the response with sequence number 9586 as seen in the
	request's transmission header, SNA Server sends the response with an incorrectly
	calculated sequence number of 11FC.
	
	Because the host gets a bad sequence number on the BIND RSP, it ignores the
	response, and continues to wait for a BIND RSP on that LU with the correct
	sequence number, stopping everyone else from using this LU.
	
	Additional query words: Lost locality Bind sequence
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : :3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
