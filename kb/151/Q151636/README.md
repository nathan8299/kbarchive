---
layout: page
title: "Q151636: BUG: Insert Object of an Imager File Causes Error or Hangs Mac"
permalink: /kb/151/Q151636/
---

## Q151636: BUG: Insert Object of an Imager File Causes Error or Hangs Mac

{% raw %}

	Article: Q151636
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b
	Operating System(s): 
	Keyword(s): kbenvkbbuglist
	Last Modified: 15-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using Microsoft Imager to insert an Imager object into a Microsoft Visual
	FoxPro for Power Macintosh general field, the machine may hang or crash with a
	"Bus Error" or a "Type 10 Error."
	
	If the machine hangs, you will be forced to press CMD+OPT+ESC and Force Quit
	Imager. If you have to Force Quit Imager, Visual FoxPro then returns the
	message:
	
	  OLE error: Application started but did not register a class factory.
	
	This typically occurs with large images.
	
	CAUSE
	=====
	
	The OLE error "Application started but did not register a class factory" is a
	symptom of low memory. Either the memory partition allocated for Microsoft
	Imager or the memory partition allocated for Visual FoxPro is too small to
	perform the requested operation.
	
	When dealing with Microsoft Imager, the problem usually occurs because the image
	is too large to load into the memory partition of Microsoft Imager. This can be
	determined by trying to insert a small image into a general field, something the
	size of "Fox.pct" in the Microsoft Visual FoxPro main folder. If this behavior
	succeeds, then the problem could be due to the size of the image you are trying
	to insert.
	
	WORKAROUND
	==========
	
	Increase the Preferred Size for both Imager and Visual FoxPro. Start by doubling
	the Preferred Size for Imager. If this does not solve the problem, then begin
	increasing the Preferred Size of Visual FoxPro in 1024K increments until the
	image is successfully inserted into the general field.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Load Microsoft Imager and open a large image (something that is over half a
	  megabyte in size and at least 256 colors).
	
	2. From the Microsoft Imager menu, select View, and then select Summary Info.
	  Check to ensure that the image's DPI setting is 72. If it is not 72, change
	  the DPI to 72 and choose OK. (This step is necessary for Visual FoxPro to
	  display the image correctly.)
	
	3. From the File menu, select Save As, and then save the file using the PICT
	  file type. Name the file TEST.PCT.
	
	4. Exit Microsoft Imager and load Visual FoxPro. To test whether Visual FoxPro
	  can display the image correctly, type the following in the Command window:
	
	        _SCREEN.Picture=TEST.PCT
	
	  and you should see the image tiled in the desktop.
	
	5. Create a table containing a general field. Browse the table and add a record
	  by pressing the CTRL+Y keys.
	
	6. From the Edit menu, select Insert Object. Select From File, and then find and
	  select TEST.PCT.
	
	If the image is large enough, you will see Visual FoxPro appear to hang.
	Actually, it is Microsoft Imager that has hung, because it does not have enough
	memory available to continue with the process. You need to Force Quit the MS
	Imager and increase the Preferred Memory size of Microsoft Imager, as instructed
	above, and try again.
	
	Additional query words: VFoxMac
	
	======================================================================
	Keywords          : kbenv kbbuglist
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac
	Version           : MACINTOSH:3.0b
	
	=============================================================================
	

{% endraw %}
