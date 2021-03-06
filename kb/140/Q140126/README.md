---
layout: page
title: "Q140126: How to Configure Microsoft 16-Bit DLC Protocol with Windows 95"
permalink: /kb/140/Q140126/
---

## Q140126: How to Configure Microsoft 16-Bit DLC Protocol with Windows 95

{% raw %}

	Article: Q140126
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the configuration of the Microsoft 16-bit DLC (MSDLC)
	protocol with Windows 95 based on a prior IBM DLC protocol installation. This
	article assumes that an NDIS2 (real-mode) network card driver is in use and that
	the MSDLC protocol will be bound to either an Ethernet or Token-Ring network
	card.
	
	MORE INFORMATION
	================
	
	The DLC protocol exposes the DLC interface commonly used for connectivity to
	AS/400 and mainframe computer systems. This protocol cannot be used for Windows
	95 client connectivity or to share files or printers with the File and Printer
	Sharing services in Windows 95.
	
	If the IBM DLC protocol is currently installed, the following steps can be used
	to install a network card driver in Windows 95 and install the MSDLC protocol
	driver:
	
	1. Disable any of the following lines that appear in the Config.sys file by
	  placing "REM" at the beginning of each such line. NOTE: Do not delete these
	  lines as they may be necessary for reference.
	
	     DEVICE=C:\<DLC_DIRECTORY>\DXMA0MOD.SYS
	     DEVICE=C:\<DLC_DIRECTORY>\DXMC0MOD.SYS  (for Token-Ring adapters)
	     DEVICE=C:\<DLC_DIRECTORY>\DXME0MOD.SYS  (for Ethernet adapters)
	     DEVICE=C:\<DLC_DIRECTORY>\DXMTOMOD.SYS  (for NetBIOS functionality)
	     DEVICE=C:\<DLC_DIRECTORY>\DXMJ0MOD.SYS  (occasionally used instead
	                                              of Dxmt0mod.sys)
	
	  An example of a disabled line should look like this:
	
	     REM DEVICE=C:\<DLC_DIRECTORY>\DXMA0MOD.SYS
	
	2. In Control Panel, double-click the Network icon.
	
	3. Click the existing IBM DLC protocol, and then click Remove.
	
	4. Click Add, click Protocol, and then click Add.
	
	5. In the Manufacturers box, click Microsoft. In the Network Protocols box,
	  click Microsoft DLC, and then click OK.
	
	6. Click OK, and then click Yes.
	
	After Windows 95 restarts, you are ready to configure the Microsoft DLC
	protocol.
	
	Configuring the Microsoft DLC Protocol
	--------------------------------------
	
	The following table outlines the standard DLC protocol settings and the
	corresponding MSDLC Advanced property parameters:
	
	Dxmt0mod.sys settings:
	
	  IBM DLC Settings/Abbreviations   MSDLC Settings
	  ---------------------------------------------------------------
	  STATIONS ST=                     stations
	  SESSIONS S=                      sessions
	  COMMANDS C=                      commands
	  DHB.SIZE DS=                     trxbufsize
	  DHB.NUMBER DN=                   trxbufsize
	  DLC.MAXOUT MO=                   maxout
	  DLC.MAXIN MI=                    maxin
	  EXTRA.SAPS ES=                   xsaps0 for first adapter
	                                   xsaps1 for second adapter
	  EXTRA.STATIONS EST=              xstations0 for first adapter
	                                   xstations1 for second adapter
	  DLC.RETRY.COUNT RC=              dlcretries
	  DLC.T1 T1=                       t1_tick_one for first adapter
	                                   t1_tick_two for second adapter
	  DLC.T2 T2=                       t2_tick_one for first adapter
	                                   t2_tick_two for second adapter
	  DLC.TI TI=                       ti_tick_one for first adapter
	                                   ti_tick_two for second adapter
	  TRANSMIT.TIMEOUT TT=             class1timeout
	
	Token-Ring Adapters
	-------------------
	
	Dxmc0mod.sys addr0, mem0, etr0, addr1, mem1, etr1
	
	This driver is used to set parameters for Token-Ring adapters that must be set
	differently depending on which Token-Ring adapter is in use. The parameters can
	be configured as follows:
	
	  addr0 - This parameter specifies the Locally Administered Address
	          (LAA) and can be set using the NETADDRESS keyword in the
	          Protocol.ini file. For additional information on Token-Ring
	          network adapters and LAAs, please see the following article
	          in the Microsoft Knowledge Base:
	
	  Q93039 Token-Ring Cards and Local Addressing with WFWG
	
	  mem0 - This parameter specifies the upper memory address used by the
	         Token-Ring adapter.
	
	  etr0 - This parameter specifies whether or not Early Token Release is
	         in use on the Token-Ring adapter.
	
	The remaining parameters are used with the second Token-Ring adapter.
	
	Ethernet Adapters
	-----------------
	
	Dxme0mod.sys addr0, wrk0, xmit_swap0, addr1, wrk1, xmit_swap1
	
	This driver is used to set parameters for an Ethernet adapter when the adapter is
	being handled by a Windows 95 NDIS2 adapter driver. The parameters can be
	configured as follows:
	
	  addr0 - This parameter can be set using the NETADDRESS keyword in the
	          Protocol.ini file.
	
	  wrk0 - This parameter specifies the work space area in kilobytes
	         (KB).
	
	  xmit_swap0 - This parameter determines whether destination address
	               bits are swapped, and whether 802.3 or Ethernet DIX 2.0
	               frames are sent.
	
	     0 - Transmit 802.2 frames and swap address bits (default).
	
	     1 - Transmit Ethernet DIX frames and swap address bits.
	
	     2 - Transmit 802.3 frames and do not swap address bits.
	
	     3 - Transmit Ethernet DIX frames and do not swap address bits.
	
	Depending on the value of xmit_swap0, you should set the MSDLC parameters as
	follows:
	
	  Dxme0mod.sys Setting   MSDLC Setting
	  ----------------------------------------------
	  xmit_swap0 = 0         usedix = 0 and swap = 1
	  xmit_swap0 = 1         usedix = 1 and swap = 1
	  xmit_swap0 = 2         usedix = 0 and swap = 0
	  xmit_swap0 = 3         usedix = 1 and swap = 0
	
	Failure to set the appropriate MSDLC parameters correctly could cause DLC
	applications to fail when trying to connect to a host system.
	
	Dxma0mod.sys
	------------
	
	This driver is primarily used for interrupt 0x5C arbitration. Therefore, no
	Windows 95 drivers need to be installed in lieu of this driver.
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
