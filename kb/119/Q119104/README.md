---
layout: page
title: "Q119104: PPT: Incorrect Title Case Change When Word Contains Apostrophe"
permalink: /kb/119/Q119104/
---

## Q119104: PPT: Incorrect Title Case Change When Word Contains Apostrophe

{% raw %}

	Article: Q119104
	Product(s): Microsoft PowerPoint for Windows
	Version(s): MACINTOSH:4.0; WINDOWS:4.0,4.0a,4.0c,7.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 15-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft PowerPoint for Windows, versions 4.0, 4.0a, 4.0c 
	- Microsoft PowerPoint for Macintosh, version 4.0 
	- Microsoft PowerPoint for Windows 95, version 7.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you use the Change Case command in PowerPoint to change text containing an
	apostrophe to Title Case, the text may capitalize incorrectly. For example, if
	you select the text
	
	  Bob's
	  Bob's car
	  Joe's
	
	and use the Change Case command to change the case to Title Case, the text may
	appear as:
	
	  Bob'S
	  Bob'S Car
	  Joe's
	
	CAUSE
	=====
	
	The problem occurs when the apostrophe in the selection is followed by a hard
	carriage return. In the above example, "Joe's" appears correctly because the
	hard carriage return was not selected during the case change. Individual words
	also display the same problem if the highlighted region includes the hard
	carriage return. This problem actually occurs with any punctuation mark,
	although apostrophes are the only punctuation marks found in the middle of
	words.
	
	RESOLUTION
	==========
	
	To work around this problem, select each word or sentence individually without
	selecting the hard carriage return character, and then change the case.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem with the products listed at the
	beginning of this article. This problem was corrected in Microsoft PowerPoint 97
	for Windows and Microsoft PowerPoint 98 Macintosh Edition.
	
	Additional query words: 4.00 4.00a 4.00c 7.00 power point powerpt change case winppt macppt
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbHWMAC kbOSMAC kbPowerPtSearch kbPowerPt700 kbZNotKeyword2 kbPowerptMacSearch kbPowerPt700Search kbPowerPt400 kbPowerPt400Mac kbPowerPt400c kbPowerPt400a
	Version           : MACINTOSH:4.0; WINDOWS:4.0,4.0a,4.0c,7.0
	Hardware          : MAC x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
