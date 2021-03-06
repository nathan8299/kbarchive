---
layout: page
title: "Q193086: Bookshelf 98 Err Msg: An Error Occurred While Attempting..."
permalink: /kb/193/Q193086/
---

## Q193086: Bookshelf 98 Err Msg: An Error Occurred While Attempting...

{% raw %}

	Article: Q193086
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup kbimu
	Last Modified: 13-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Bookshelf 98 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to play an animation in Bookshelf 98, you may receive the
	following error message:
	
	  An error occurred while attempting to load the movie.
	
	If you click OK, you receive the following error message
	
	  Bsmmplyr.exe: Couldn't open
	  <drive>:\Bookshelf98\Books\Mm\<filename>
	
	where <drive> is the letter of the CD-ROM drive that contains the Bookshelf
	98 CD-ROM, and <filename> is the name of the animation file that you
	attempted to play.
	
	CAUSE
	=====
	
	This behavior can occur if you copy the contents of the Bookshelf 98 CD-ROM to a
	folder with a long file name on the hard disk and then install and run Bookshelf
	from that folder.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods.
	
	Run Bookshelf 98 from the CD-ROM Drive
	--------------------------------------
	
	To run Bookshelf 98 from the CD-ROM drive, follow these steps:
	
	1. Remove Bookshelf. To do this, follow these steps:
	
	  a. Click Start, point to Settings, and then click Control Panel.
	
	  b. Double-click Add/Remove Programs.
	
	  c. Click Microsoft Bookshelf 1998 (Remove Only), and then click Add/Remove.
	
	  d. Follow the instructions on the screen to remove Bookshelf 98.
	
	  e. Close Control Panel.
	
	2. Delete the folder in which you copied the contents of the Bookshelf 98
	  CD-ROM.
	
	  For information about how to delete folders, click Start, click Help, click
	  the Index tab, type "deleting, folders" (without the quotation marks), and
	  then click Display.
	
	  NOTE: If you are using Microsoft Windows 98, click Start, click Help, click
	  the Index tab, type "deleting files, folders" (without the quotation marks),
	  and then click Display.
	
	3. Insert the Bookshelf 98 CD-ROM into the CD-ROM drive.
	
	4. Follow the instructions on the screen to install and run Bookshelf 98.
	
	Rename the Folder Containing the Contents of the Bookshelf 98 CD-ROM
	--------------------------------------------------------------------
	
	To rename the folder containing the contents of the Bookshelf 98 CD-ROM, follow
	these steps:
	
	1. Remove Bookshelf. To do this, follow these steps:
	
	  a. Click Start, point to Settings, and then click Control Panel.
	
	  b. Double-click Add/Remove Programs.
	
	  c. Click Microsoft Bookshelf 1998 (Remove Only), and then click Add/Remove.
	
	  d. Follow the instructions on the screen to remove Bookshelf 98.
	
	  e. Close Control Panel.
	
	2. Verify that the folder containing the contents of the Bookshelf 98 CD-ROM is
	  located inside the root folder of the hard disk. If this folder is located
	  inside another folder, move the folder containing the contents of the
	  Bookshelf 98 CD-ROM to the root folder of the hard disk.
	
	  For information about how to move folders, click Start, click Help, click the
	  Index tab, type "moving, files" (without the quotation marks), and then click
	  Display.
	
	  NOTE: If you are using Microsoft Windows 98, click Start, click Help, click
	  the Index tab, type "moving files, folders" (without the quotation marks),
	  and then click Display.
	
	3. Right-click the folder that containing the contents of the Bookshelf 98
	  CD-ROM, and then click Rename.
	
	4. Type "Book98cd" (without the quotation marks), and then press ENTER.
	
	5. Install Bookshelf 98 from the renamed folder. To do this, follow these
	  steps:
	
	  a. Click Start, and then click Run.
	
	  b. In the Open box, type the following line, and then click OK
	
	        <drive>:\Book98cd\setup.exe
	
	     where <drive> is the letter of the hard disk on which the Book98cd
	     folder is located.
	
	  c. Follow the instructions on the screen to install Bookshelf 98.
	
	MORE INFORMATION
	================
	
	Bookshelf uses the Bsmmplyr.exe file to play animations. The Bsmmplyr.exe file
	is a 16-bit program that does not work with long file names.
	
	Additional query words: multi multi-media media mm
	
	======================================================================
	Keywords          : kberrmsg kbsetup kbimu 
	Technology        : kbHomeMMsearch kbBookshelfSearch kbBookShelf1998
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
