---
layout: page
title: "Q303909: MechCommander 2.0: Known Issues"
permalink: /kb/303/Q303909/
---

## Q303909: MechCommander 2.0: Known Issues

{% raw %}

	Article: Q303909
	Product(s): Microsoft Home Games
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kb3rdparty kberrmsg kbsound kbimu
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MechCommander 2.0, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses known issues that you may experience with Microsoft
	MechCommander 2.0.
	
	MORE INFORMATION
	================
	
	Issue 1
	-------
	
	When you start MechCommander, you may receive the either of the following error
	messages:
	
	  Cannot find DirectInput functions
	
	-or-
	
	  STOP: Cannot CreateNetLib
	
	This behavior can occur if you choose not to restart your computer after you
	install MechCommander, and you then immediately attempt to start MechCommander.
	
	Issue 2
	-------
	
	When you use the MechCommander Editor, you may receive the following error
	message:
	
	  [ASSERT 0] No components in the purchase file.
	
	This behavior occurs if you name your mission "Purchase01". You must select a
	different name in this case.
	
	Issue 3
	-------
	
	When you are playing a multiplayer game, you cannot download custom insignias,
	even though you could download them before.
	
	The Unit Insignia list in Player Preferences (multiplayer) only displays the
	first 125 insignias. To clear old insignia files, remove them from the
	data\multiplayer\insignia folder.
	
	Issue 4
	-------
	
	If you are running Microsoft Windows 2000, you may receive the following error
	message:
	
	  Your system is low on virtual memory. Windows is increasing the size of your
	  virtual memory paging file. During this process, memory requests for some
	  applications may be denied.
	
	To resolve this issue, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System, and then click the Advanced tab.
	
	3. Click Performance Options, and then click Change under Virtual Memory.
	
	4. Under "Paging File Size for Selected Drive", change the initial size to 250
	  MB, change the maximum size to 500 MB, and then click Set.
	
	5. Click OK three times.
	
	Issue 5
	-------
	
	If you are running Windows 2000, you may experience choppy playback of audio or
	the program may stop responding (hang). These symptoms occur if you are using
	cards based on the Aureal Vortex 2 chipset.
	
	To resolve this issue, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click "Sounds and Multimedia", and then click the Audio tab.
	
	3. Under Sound Playback, click Advanced, and then click the Performance tab.
	
	4. Drag the Hardware Acceleration slider to the left two notches, and then click
	  OK twice.
	
	Issue 6
	-------
	
	If you quit Microsoft NetMeeting 3.01 improperly, or if Remote Desktop Sharing is
	enabled, Direct3D functionality is disabled. When you restart the computer,
	Direct3D functionality is not restored.
	
	NetMeeting 3.01 automatically disables Direct3D functionality when it starts.
	When you quit NetMeeting properly, it restores Direct3D functionality. To
	resolve this issue, start NetMeeting 3.01, and then quit it properly.
	
	Issue 7
	-------
	
	Norton Antivirus 2001 slows video playback and goes the game to start slowly.
	With Norton Antivirus 2001 Autoprotect running, it may take four to five times
	longer than normal to start MechCommander. To resolve this issue, disable Norton
	Antivirus before you start the game.
	
	Issue 8
	-------
	
	The IntelliPoint ClickLock feature conflicts with right-click mouse camera
	control.
	
	When you adjusting camera perspective with the right mouse button, the ClickLock
	feature is engaged. To resolve this issue, turn off the ClickLock feature when
	you play MechCommander.
	
	Issue 9
	-------
	
	When you start MechCommander and you are using an ATI Rage Fury Maxx card, the
	computer may stop responding after the opening movies, during the fade into the
	menu.
	
	This behavior occurs with the ATI Rage Fury Maxx card with driver version
	4.12.01.7942. To resolve this issue, use version 7925 of the driver.
	
	If you are unable to see in-game videos, or receive an error message stating:
	
	  MC2RES.DLL 0 NOT FOUND
	
	please see the following article:
	
	  Q303913 MechCommander 2.0: You Cannot See In-Game Videos
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: msgame mech commander mech2
	
	======================================================================
	Keywords          : kb3rdparty kberrmsg kbsound kbimu 
	Technology        : kbGamesSearch kbMSNSearch kbMechCommSearch kbMechCommander200
	Version           : :1.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
