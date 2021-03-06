---
layout: page
title: "Q104232: Windows NT Remote Access Client Information"
permalink: /kb/104/Q104232/
---

## Q104232: Windows NT Remote Access Client Information

{% raw %}

	Article: Q104232
	Product(s): Microsoft Windows NT
	Version(s): 3.1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 27-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	-------------------------------------------------------------------------------
	
	The recommended Remote Access Client for Windows NT is RAS 1.1a. This
	package is available at no charge to owners of Windows NT. See the
	following for more information. This article also contains additional
	information on older RAS client packages.
	
	RAS CLIENT INFORMATION
	----------------------
	
	RAS 1.1a:
	
	RAS 1.1a is the recommended client software to use with Windows NT
	Remote Access Servers. If you own Windows NT or Windows NT Advanced
	Server, you can obtain RAS 1.1a for no charge through a fulfillment
	coupon located in the back of the Windows NT "System Guide." RAS 1.1a
	will also be available through the individual MS Network License
	packages. You can install RAS 1.1a on any supported operating system
	that has MS Network License. For example, all purchased copies of
	Windows for Workgroups 3.1 have the right to use RAS 1.1a at no
	charge.
	
	MS-DOS clients need to own a MS Network License such as MS LAN Manager
	or the Microsoft License Pack for Networks.
	
	In general, RAS 1.1a now supports flow control, error correction and
	modem data compression. In addition, it has an expanded supported
	modem list to match up with Windows NT RAS.
	
	RAS 1.1a contains two versions of the MODEMS.INF file. MODEMS.INF
	contains standard initialization strings. MCOMP.INF contains
	initialization strings with flow control, error correction and modem
	compression enabled for most modems.
	
	For more information, please query on the following words in the
	Microsoft Knowledge Base:
	
	  ras and 1.1a and enhancements and fixes
	
	RAS 1.1:
	
	RAS 1.1 was only available as a complete Server and Client package for
	use with MS OS/2 LAN Manager server and LAN Manager clients. Major
	enhancements of RAS 1.1 over 1.0 include: X.25 support, Windows for
	Workgroups 3.1 direct installation support, and so on.
	
	All clients running RAS 1.1 should upgrade to RAS 1.1a.
	
	All RAS 1.1 OS/2 LAN Manager servers must stay at this level or
	upgrade to Windows NT Advanced Server.
	
	RAS 1.0:
	
	This is the original Remote Access Product and is no longer for sale
	by Microsoft. RAS 1.0 was only available as a complete Server and
	Client package for use with MS OS/2 LAN Manager server and LAN Manager
	clients. Any RAS 1.0 servers or clients should upgrade.
	
	RAS OPERATING SYSTEMS
	---------------------
	
	Windows for Workgroups 3.1:
	
	Windows for Workgroups 3.1 is its own MS Network client. It does not
	require MS LAN Manager. RAS 1.1a should be installed directly with
	Windows for Workgroups 3.1. RAS 1.1 will recognize Windows for
	Workgroups 3.1 clients by default, but version 1.1a is recommended.
	RAS 1.0 is not recommended for this client.
	
	Microsoft Windows 3.1:
	
	Microsoft Windows 3.1 requires MS LAN Manager 2.x software. You can
	individually purchase MS Network License Packs for your MS-DOS
	Clients. RAS 1.1a is recommended client software. The best solution
	for this operating system is to upgrade Windows for Workgroups and RAS
	1.1a.
	
	
	MS-DOS 3.3-6.0:
	
	MS-DOS versions 3.3 through 6.0 require MS LAN Manager 2.x software.
	You can individually purchase MS Network License Packs for your MS-DOS
	Clients. RAS 1.1a is recommended client software.
	
	MS OS/2 1.3x:
	
	Microsoft OS/2 versions 1.3x require MS LAN Manager 2.x software for
	MS OS/2. This is only available as part of MS LAN Manager Server
	package.
	
	In order to use this as a RAS client, you must get RAS 1.1--not RAS
	1.1a. RAS 1.1a does not support OS/2. RAS 1.1 is only available as a
	separate server package for MS LAN Manager server. It includes both
	client and server software for MS OS/2 and MS-DOS.
	
	OS/2 2.x:
	
	There is no RAS support for OS/2 2.x.
	
	Windows NT:
	
	Windows NT includes both RAS client and server software. Windows NT
	RAS is backward compatible with all previous versions.
	
	CLIENTS TABLE
	-------------
	
	The following table applies only to RAS Client packages and platforms.
	The left column contains the operating system and the required MS
	Network Client version. The column titles are the various RAS packages
	that have been produced by Microsoft.
	
	The table:
	
	Yes = Best Recommended combination.
	OK  = It will work but it is not recommended.
	No  = Will not work or is not supported.
	
	The values:
	
	The values in the table are the number of COM ports that are supported
	under each combination.
	
	NOTE: This table does not represent RAS interoperablity.
	
	Operating System       RAS WinNT    RAS 1.1a       RAS 1.1       RAS 1.0
	
	:
	
	MS-DOS v3.3-6.0           No           Yes            OK           OK
	MS LAN Manager 2.x                      2             2            2
	
	MS OS/2 v1.3x             No           No             Yes          OK
	MS LAN Manager 2.x                                    16           16
	
	IBM OS/2 v2.x             No           No             No           No
	MS LAN Manager 2.x
	
	MS Windows 3.1            No           Yes            OK           OK
	MS LAN Manager 2.x                      2             2            2
	
	Windows for               No           Yes            OK           No
	Workgroups v3.1                         2             2
	
	Windows NT v3.1           Yes          No             No           No
	
	                         64
	
	Windows NT                Yes          No             No           No
	Advanced Server           64
	
	RAS Servers            RAS WinNT    RAS 1.1a       RAS 1.1       RAS 1.0
	
	:
	
	RAS WinNT              ABCDEFG      BCE            E
	
	RAS 1.1a               BCE          E              E
	
	RAS 1.1                E            E              E
	
	RAS 1.0
	
	NOTES:
	
	A = RAS Software Compression. Windows NT RAS introduced a new RAS
	   feature called Software Compression. This allows data to be compressed
	   before it is transferred. This will work on any modem even those that
	   do not support modem hardware compression. Depending on the data type,
	   Software Compression can offer 2 to 1 compression ratio or higher.
	   This feature offers the best RAS performance available on any
	   platform. It is not recommended to use both hardware and software
	   compression at the same time.
	
	B = Flow Control, Error Correction and Modem Compression. Hardware Flow
	   Control[RTS\CTS] is available in RAS 1.1a and later. With Flow
	   Control enabled, RAS can also take advantage of error correction and
	   modem compression. This can significantly improve performance and
	   throughput.
	
	C = Enhanced Supported Modem List. Windows NT Supports over 100
	   different modem models. RAS 1.1a supports nearly that many.
	
	D = ISDN Support. Integrated Services Digital Network support.
	   Drivers are included for Digiboard ISDN cards. Supports up to 128K
	   bps.
	
	E = X.25 public switch network support.
	
	F = 16550 FIFO UART chip support.
	
	G = Support for 3rd party external security hosts.
	
	
	Additional query words: wfw wfwg prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW310 kbWinNTSsearch kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : :3.1
	
	=============================================================================
	

{% endraw %}
