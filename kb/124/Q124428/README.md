---
layout: page
title: "Q124428: NE2000 and Panasonic CD-ROM Fails when Used Simultaneously"
permalink: /kb/124/Q124428/
---

## Q124428: NE2000 and Panasonic CD-ROM Fails when Used Simultaneously

{% raw %}

	Article: Q124428
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.5 
	- Microsoft Windows NT Server version 3.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You experience a failure loading and simultaneously using a NE2000 (or
	compatible) network adapter and a Panasonic CD-ROM drive attached to a Sound
	Blaster 16 adapter.
	
	CAUSE
	=====
	
	This problem occurs when the NE2000 (or compatible) network adapter is
	configured to use an I/O port address greater than 300H.
	
	RESOLUTION
	==========
	
	To correct this problem, do one or both of the following:
	
	- Configure the I/O port address of the NE2000 (or compatible) network adapter
	  to less than 300H. The NE2000 driver shipped with Windows NT version 3.5 only
	  supports the I/O port address of 280H under 300H. To change the address
	  setting, do the following:
	
	  1. Run Control Panel and choose Network.
	
	  2. Select the NE2000 driver under Installed Adapter Cards and choose
	     Configure.
	
	  3. Change the I/O Address to 280H and choose OK.
	
	  4. Shutdown Windows NT.
	
	  5. Either run the Configuration Utility or change jumpers on the NE2000 (or
	     compatible) network adapter, configuring it to use the I/0 Port address of
	     280H.
	
	  6. Restart Windows NT.
	
	
	- If the I/O port address of 280H does not work, change it to a another one
	  either by using the Configuration Utility or changing the jumpers on the
	  network adapter. In Windows NT, you must modify the Registry to change to an
	  address other than 280H.
	
	  WARNING: Using Registry Editor incorrectly can cause serious, system- wide
	  problems that may require you to reinstall Windows NT to correct them.
	  Microsoft cannot guarantee that any problems resulting from the use of
	  Registry Editor can be solved. Use this tool at your own risk.
	
	  1. Run Registry Editor (REGEDT32.EXE).
	
	  2. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  SYSTEM\CurrentControlSet\Services\NE2000x\Parameters
	
	     (where x is the number of the NE2000 network adapter)
	
	  3. Select the IoBaseAddress value.
	
	  4. From the Edit menu, choose DWORD.
	
	  5. In the Data field, type the hexadecimal address configured for the network
	     adapter. For Radix, select Hex.
	
	  6. Close Registry Editor.
	
	  7. Shutdown and restart Windows NT.
	
	MORE INFORMATION
	================
	
	To prevent hardware conflicts due to adapter configuration, use one of the
	following supported settings for the NE2000 (or compatible) network interface
	card (NIC) and the Sound Blaster 16 adapter:
	
	  Supported   NE2000          Sound Blaster 16
	  ---------------------------------------------------------------
	  IRQs        3 (Default)     5 (Default)
	              2, 4, 5, 10,    2, 7, 10
	              11, 12, 15
	
	  I/O Ports   300h (Default)  Sound DSP, MIDI and Mixer:
	              240h, 280h,     220h (Default), 240h, 260h, 280h
	              2C0h, 320h,     Games Interface/Joystick:
	              340h            200h (Default)
	                              MPU401 External MIDI Interface:
	                              300h (Default), 330h
	                              Proprietary or SONY CD-ROM:
	                              230h, 250h, 270h, 290h
	                              Mitsumi CD-ROM (multi-CD versions):
	                              310h, 320h, 340h, 350h
	                              OPL3 Compatible:
	                              388h
	
	The third-party products discussed here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: prodnt IDE sb creative labs
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search
	
	=============================================================================
	

{% endraw %}
