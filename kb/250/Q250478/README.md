---
layout: page
title: "Q250478: Streets 98 Err Msg: Application Can't Find GPS on Your System..."
permalink: /kb/250/Q250478/
---

## Q250478: Streets 98 Err Msg: Application Can't Find GPS on Your System...

{% raw %}

	Article: Q250478
	Product(s): Microsoft Automap
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kberrmsg kbui kbimu
	Last Modified: 12-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Expedia Streets 98 
	- Microsoft Expedia Streets 98 Deluxe, version 1.0 
	- Microsoft Expedia Trip Planner 98 
	- Microsoft Streets & Trips 2002, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you click GPS on the Tools menu in one of the programs listed at the
	beginning of this article, you may receive the following error message:
	
	  The Application could not find a GPS on your system. Check to ensure that
	  your receiver is attached properly.
	
	CAUSE
	=====
	
	This behavior can occur if the following conditions are true:
	
	- Microsoft ActiveSynch 3.0 is installed on your computer.
	
	- The communications (COM) port to which you connect your GPS device is the
	  same COM port that ActiveSynch uses to establish a serial connection.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods.
	
	Connect Your GPS Device to a Different COM Port
	-----------------------------------------------
	
	If your computer has two COM ports, connect your GPS device to a COM port that is
	different from the one to which you connect your Microsoft Windows CE device.
	
	Temporarily Disable ActiveSynch
	-------------------------------
	
	To temporarily disable ActiveSynch:
	
	1. Click Start, point to Programs, and then click Microsoft ActiveSynch.
	
	2. On the File menu, click Connection Settings.
	
	3. Click to clear the "Allow serial cable or infrared connection to this COM
	  port" check box.
	
	4. Click OK.
	
	NOTE: You need to select the "Allow serial cable or infrared connection to this
	COM port" check box before you synchronize your Windows CE device.
	
	Additional query words: auto-map amap
	
	======================================================================
	Keywords          : kberrmsg kbui kbimu 
	Technology        : kbHomeProdSearch _IKkbbogus kbExpediaSearch kbExpediaStreets98 kbExpediaStreets98del kbExpediaStreets2002
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
