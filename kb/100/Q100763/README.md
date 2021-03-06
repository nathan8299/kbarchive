---
layout: page
title: "Q100763: Using Compressed Floppy Disks without a Compressed Hard Disk"
permalink: /kb/100/Q100763/
---

## Q100763: Using Compressed Floppy Disks without a Compressed Hard Disk

{% raw %}

	Article: Q100763
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 16-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.22 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	
	This information applies to both Microsoft DoubleSpace and Microsoft DriveSpace.
	For MS-DOS 6.22, use DRVSPACE in place of DBLSPACE for commands and filenames.
	
	You want to use DoubleSpace-compressed floppy disks without compressing your hard
	disk, but when you run DBLSPACE, the initial setup screen does not provide an
	option to compress only a floppy disk.
	
	When you try to compress a floppy disk with DBLSPACE /COMPRESS <drive:>,
	you receive the following message:
	
	  DoubleSpace cannot compress a floppy drive until you have installed
	  DoubleSpace on your computer. To install DoubleSpace, type DBLSPACE at the
	  command prompt.
	
	When you try to mount an already compressed floppy disk with DBLSPACE /MOUNT
	<drive:>, you receive the following message:
	
	  There are no more drive letters reserved for DoubleSpace to use.
	  To add more drive letters, choose the Options command from the Tools menu.
	
	WORKAROUND
	==========
	
	To use DoubleSpace-compressed floppy disks without compressing the hard disk,
	use one of the workarounds described below. Both procedures create a
	DBLSPACE.INI file in the root directory of your startup drive and cause
	DBLSPACE.BIN to remain in memory after startup. Note that the DBLSPACE.BIN
	driver uses up to 54 kilobytes (K) of memory. You can not use compressed floppy
	disks without loading DBLSPACE.BIN into memory. For more information on
	DBLSPACE.BIN and memory, refer to your printed MS-DOS documentation and online
	Help.
	
	Workaround 1
	------------
	
	Create a small, new DoubleSpace drive and then delete it. This creates the
	DBLSPACE.INI file and loads DBLSPACE.BIN into memory so that you can read the
	compressed floppy disk drive.
	
	To do this:
	
	1. To run DoubleSpace, type "dblspace" (without the quotation marks) at the
	  MS-DOS command prompt.
	
	2. Choose Custom Setup.
	
	3. Choose "Create a new empty compressed drive."
	
	4. Select the drive you want to use. (DoubleSpace will use the free space on
	  this drive to create a new compressed drive.)
	
	5. When DoubleSpace displays the amount of free space to leave on the drive, use
	  the UP ARROW key to move the highlight bar to the "Free space" setting and
	  then press ENTER. This allows you to change the "Free space" setting.
	
	6. When prompted for the amount of free space to leave on the drive, type a
	  number LARGER than your hard disk drive and press ENTER.
	
	7. After DoubleSpace tells you the maximum amount free space you can leave on
	  your drive, type in that number. For example, if DoubleSpace tells you the
	  maximum amount of free space is 95.55 megabytes (MB), leave 95 MB of free
	  space.
	
	8. Choose Continue.
	
	9. Press the "C" key to create the compressed drive.
	
	10. After DoubleSpace completes, if you do not want to keep the new compressed
	  drive you created, run DBLSPACE and delete the new drive by selecting the
	  Delete command from the Drive menu.
	
	  Alternatively, you can delete the drive by using the following command:
	
	      dblspace /delete <drive:>
	
	  where <drive:> is the new compressed drive.
	
	Now you can use compressed floppy disks. For example, to compress the floppy disk
	in drive A:, type the following at the command prompt and press ENTER:
	
	  " dblspace /compress a:" (without the quotation marks)
	
	To access an existing compressed floppy in drive A:, type the following at the
	MS-DOS command prompt and press ENTER:
	
	  " dblspace /mount a:" (without the quotation marks)
	
	Workaround 2
	------------
	
	1. Create a C:\DBLSPACE.INI file (where C is your startup disk) with a text
	  editor such as MS-DOS Editor. The DBLSPACE.INI file should contain the
	  following two lines:
	
	     MaxRemovableDrives=2
	     LastDrive=F
	
	  NOTE: LastDrive= must be set to one letter beyond your last logical drive
	  letter. For example, if your last drive is E, use LastDrive=F in your
	  DBLSPACE.INI file.
	
	2. Copy DBLSPACE.BIN from your DOS directory to the root directory of your
	  startup (boot) drive. For example:
	
	     copy c:\dos\dblspace.bin c:\
	
	3. Restart your computer.
	
	Now you can use compressed floppy disks. For example, to compress the floppy disk
	in drive A:, type the following at the command prompt and press ENTER:
	
	  " dblspace /compress a:" (without the quotation marks)
	
	To access an existing compressed floppy in drive A:, type the following at the
	MS-DOS command prompt and press ENTER:
	
	  " dblspace /mount a:" (without the quotation marks)
	
	MORE INFORMATION
	================
	
	To remove the DBLSPACE driver from memory, delete the DBLSPACE.BIN file from the
	root of your boot drive and then restart your computer. You can use the DELTREE
	command to delete DBLSPACE.BIN:
	
	  deltree c:\dblspace.bin
	
	IMPORTANT: Once you delete DBLSPACE.BIN and restart your computer, you can not
	create new compressed floppies or access existing compressed floppies.
	
	REFERENCES
	==========
	
	Microsoft MS-DOS "User's Guide," version 6.0
	
	MS-DOS Help, DBLSPACE topic
	
	Additional query words: 6.00 6.20 double space drive how to mount drvspace access compression
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.22
	
	=============================================================================
	

{% endraw %}
