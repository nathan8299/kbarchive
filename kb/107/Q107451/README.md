---
layout: page
title: "Q107451: TN3270 Incorrectly Formats LU-SSCP Data From The Host"
permalink: /kb/107/Q107451/
---

## Q107451: TN3270 Incorrectly Formats LU-SSCP Data From The Host

{% raw %}

	Article: Q107451
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11
	Operating System(s): 
	Keyword(s): kbinterop kbnetwork
	Last Modified: 15-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 2.11, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When the TN3270 Server converts LU-SSCP clear-text-format data from the host
	into 3270 datastream format because TN3270 clients expect to receive data in
	3270 datastream format from the host, the TN3270 Server incorrectly inserts new
	rows causing the bottom rows to wrap around to the top of the screen.
	
	CAUSE
	=====
	
	The TN3270 Server formatting code does not correctly handle the newline
	character at the end of a line.
	
	
	RESOLUTION
	==========
	
	Microsoft has updated the file <tnroot>\TN3SERVR.EXE to correct this
	problem.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server for Windows NT. This
	problem was corrected in the latest SNA Server for Windows NT, 2.11 U.S. Service
	Pack. For information on obtaining the Service Pack, query on the following word
	in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbinterop kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.11
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
