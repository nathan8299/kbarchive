---
layout: page
title: "Q231258: SMS: Smsmon32.exe and Smswiz32.exe Hang Client Computers"
permalink: /kb/231/Q231258/
---

## Q231258: SMS: Smsmon32.exe and Smswiz32.exe Hang Client Computers

{% raw %}

	Article: Q231258
	Product(s): Microsoft Systems Management Server
	Version(s): WINDOWS:95; winnt:2.0,4.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbAdvertisement kbSoftwareDist
	Last Modified: 18-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you choose a custom icon when you create a program for a software
	distribution package, Advertised Programs Monitor (Smsmon32.exe) or the
	Advertised Programs wizard (Smswiz32.exe) may stop responding (hang).
	
	A noticeable side effect can occur when a user attempts to open a file using a
	file association. When the user double-clicks a file attachment in e-mail or a
	data file in Windows Explorer, nothing may happen. If you end the Smsmon32.exe
	task, the program starts as expected.
	
	This problem affects both Microsoft Windows NT and Microsoft Windows 95/98
	clients.
	
	CAUSE
	=====
	
	This problem occurs if you use a 256-color icon.
	
	WORKAROUND
	==========
	
	When you create the program, configure it to use an icon with less than 256
	colors. Note that using the Notepad.exe icon also does not cause the problem to
	occur.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	When the problem occurs, one Smsmon32 or Smswiz32 thread stops on the following
	entry in the Smsmon32.log or Smswiz32.log file (located in the client's
	%Windows%\Ms\Sms\Logs folder):
	
	  IPC UI      : Sending message IPC_CS_MESSG_REQUEST_PROGRAM_CAPICON~
	
	Smsmon32.exe or Smswiz32.exe hangs repeatedly until the program is disabled or
	the advertisement is deleted.
	
	To disable a program:
	
	1. Open the program's properties.
	
	2. Click the Advanced tab.
	
	3. Click to select the "Disable this program on computers where it is
	  advertised" check box.
	
	Additional query words: prodsms outlook lotus notes attached file lock up freeze winnt win95 win98 resource explorer associated smsfaqtop
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbAdvertisement kbSoftwareDist 
	Technology        : kbWinNTsearch kbWinNTWsearch kbSMSSearch kbWin95search kbWin98search kbExchange400 kbWin95 kbWin98 kbFunImagination200
	Version           : WINDOWS:95; winnt:2.0,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
