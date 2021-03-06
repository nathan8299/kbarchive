---
layout: page
title: "Q160068: WD97: Optimizing Microsoft Word 97"
permalink: /kb/160/Q160068/
---

## Q160068: WD97: Optimizing Microsoft Word 97

{% raw %}

	Article: Q160068
	Product(s): Word 97 for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): word97kbfaq
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following issues affect overall Word performance.
	
	If you are unfamiliar with a term used in this article, see the glossary at the
	end of this article.
	
	MORE INFORMATION
	================
	
	System Requirements for Word 97
	-------------------------------
	
	To use Microsoft Word 97, you need the following:
	
	- Personal or Multimedia computer with a 486 or higher processor.
	
	- Microsoft Windows 95 operating system or Windows NT Workstation 3.51 with
	  Service Pack 5 or later (will not run on earlier versions). To use Microsoft
	  Word 97 with Windows NT Workstation 4.0, you must install Service Pack 2
	  (SP2) or later.
	
	- 8 megabytes (MB) of RAM for use on Windows; 16 MB of memory for use on
	  Windows NT Workstation.
	
	- 20-60 MB of hard disk space required; 46 MB required for typical
	  installation, depending on configuration (use the Office Upgrade Wizard
	  during Setup to maximize free disk space).
	
	- 8 MB of additional memory required to run WordMail.
	
	NOTE: See the product literature or the Ofread8.txt and Wdread8.txt files for a
	complete list of requirements. Both files are included on your CD in the Office
	folder.
	
	Increase RAM
	------------
	
	The amount of memory Word 97 needs to run at top speed depends on a variety of
	factors, such as how many other applications are running at the same time and
	what types of operations Word performs. When other applications are competing
	for memory, you can usually improve performance significantly by running with
	more than the required amount.
	
	Word requires 8 MB of memory for use on Windows 95 (8 MB of additional memory
	required to run WordMail). However, for best performance on Windows 95, if you
	plan to run additional applications simultaneously, additional memory may be
	required.
	
	If you regularly work with large documents (50 pages and larger) or use many
	graphics or embedded objects in your documents, adding RAM will yield the most
	dramatic improvement to Word's operating speed. If your computer has 16 MB or
	more of RAM, Word will run faster, and you will also be able to run another
	large application (such as Microsoft Excel) at the same time and interact with
	it from Word.
	
	TIP: Make sure that you aren't using any of your RAM for a RAM drive.
	
	Use Disk Defragmenter to Speed Up Your Hard Disk
	------------------------------------------------
	
	You should occasionally use a utility such as the Windows Disk Defragmenter to
	defragment the hard disk. You can use Disk Defragmenter to rearrange files and
	unused space on your hard disk so that programs run faster. This and other
	third-party disk optimization software helps to minimize the area on the disk in
	that Windows 95 needs to look for information. As with any such utilities,
	always make back up copies of important files before you run the program. For
	more information about using Disk Defragmenter or other third-party disk
	optimization software, see your Windows or third- party documentation.
	
	Optimize Virtual Memory Use
	---------------------------
	
	NOTE: Unless you are an advanced user, it is recommended to let Windows 95 manage
	your Virtual Memory Settings option on the Performance tab of the My Computer
	property sheet. You should use the default virtual memory settings whenever
	possible.
	
	With virtual memory, an application sees a large, continuous block of primary
	memory (RAM) that, in reality, is a much smaller block of primary memory
	supplemented by secondary memory (such as a hard disk). To temporarily free up
	space in RAM, blocks of data (called pages) are moved between RAM and a swap
	file located on the hard disk.
	
	By default, the Windows 95 swap file is dynamic, so it can shrink or grow based
	on available disk space and the operations performed on the system. Also, the
	swap file can occupy a fragmented region of the hard disk with no substantial
	performance penalty. A dynamic swap file is usually the most efficient use of
	resources. The simplest way to ensure high virtual memory performance is to make
	sure that the disk containing the swap file has ample free space so that the
	swap file size can shrink and grow as needed.
	
	In Windows 3.x, enhancing performance by changing virtual memory settings is
	quite common. Because the Windows 95 swap file is dynamic, the need to change
	virtual memory settings is less common. However, in some situations adjusting
	virtual memory settings can improve performance. If you've already tried
	deleting unnecessary files, and you still have a performance problem, try
	changing the Windows 95 default virtual memory settings.
	
	If you have more than one drive available, you may get better performance if you
	specify that Windows locate the swap file on a drive other than the default in
	the following cases:
	
	- If the default drive doesn't have much free disk space, and another local
	  drive has space available.
	
	- If another local drive is available that is faster than the current drive
	  (unless that disk is already heavily used).
	
	You also may get better performance if you specify the minimum disk space
	available for virtual memory to be at least 25 MB minus available RAM. For
	example, if a computer has 12 MB of RAM, you should specify at least 13 MB of
	virtual memory. You may want to specify more if several large applications will
	be run at the same time.
	
	For information about changing Windows 95 virtual memory settings, see the
	"virtual memory settings" topic in Windows 95 Help.
	
	Set Your Computer to Use Fewer Fonts, or to Use a Font Organizing Utility
	-------------------------------------------------------------------------
	
	The more fonts installed in Windows, the slower Windows and many applications
	start because these programs read the entire font list at startup. Word does not
	process the font list at startup; however, the impact of a large number of fonts
	may be felt at other times such as the first time you print. In addition,
	certain dialog boxes (such as the Font dialog box or the Insert Symbol dialog
	box) take longer to appear the first time in a session with a large number of
	fonts installed in a system. Furthermore, when Word needs to perform some
	complex actions, fonts use additional memory and file resources.
	
	Consider Setting Your Monitors to Use Only 16 or 256 Colors
	-----------------------------------------------------------
	
	Set your computer's monitor to use the correct video driver for faster screen
	display. You may not need the highest resolution video driver and the up to 16
	million colors your video driver supports. Additional color support in a video
	driver can dramatically decrease the speed of screen updates when you scroll or
	update graphics.
	
	For writing reports and working with spreadsheets, you may need only 16 to 256
	colors, so you can switch to a video driver that supports a lower resolution and
	fewer colors. You can always switch back if there is no change in performance or
	if your work requires additional video capabilities.
	
	For additional information about video memory requirements for different video
	resolutions in Windows 95, please see the following article in the Microsoft
	Knowledge Base:
	
	  
	
	  Q132328 Description of Video RAM Required for Higher Resolutions
	
	Work with Word and Files on Uncompressed Drives
	-----------------------------------------------
	
	You can use DriveSpace or other third-party utilities to compress both hard and
	floppy disks to create more free space for files. While these utilities increase
	the disk space available to you, they can slow performance of software running
	from that drive, especially if the compression utility is not optimized.
	
	The primary reason for performance degradation while running compression software
	such as DoubleSpace is that each time a read or write is made from or to the
	hard disk, data must be decompressed or compressed. This decompression or
	compression of data places additional demand on the processor in your computer.
	Computers with faster processors most likely will not experience performance
	degradation after compression software is installed.
	
	For additional information, please see your third-party documentation or if you
	are using DriveSpace, the following article in the Microsoft Knowledge Base:
	
	  
	
	  Q97741 Optimizing DoubleSpace on Your Computer
	
	Work with Files on a Local Disk, Not From Floppy Disk
	-----------------------------------------------------
	
	Running Word from or working with files located on a floppy disk may be slower
	than working from a local hard disk. Avoid working on files located on a floppy
	disk. Copy them locally instead.
	
	Turn Off Use Printer Metrics to Lay Out Document to Improve Scrolling Speed
	---------------------------------------------------------------------------
	
	For converted documents, turn off Use Printer Metrics to Lay Out Document to
	improve scrolling speed. With this option off, Word scrolls faster because the
	program does not need to check printer settings to calculate formatting and
	layout.
	
	NOTE: This option is on by default in converted documents to preserve exact Word
	95 or 6.x document formatting. Turning off this option may cause minor changes
	in line wrapping or document pagination.
	
	To change this option, follow these steps:
	
	1. On the Tools menu, click Options, and then click the Compatibility tab.
	
	2. Select Microsoft Word 6.0/95 from the Recommended Options for box.
	
	3. Select or clear the Use printer metrics to lay out document check box.
	
	Don't Use Wallpaper on a Low-Memory Computer
	--------------------------------------------
	
	If the Windows desktop has a wallpaper (full-screen background) bitmap and the
	computer has only 8-12 MB installed memory, replace the wallpaper with a solid
	color or pattern bitmap, or no bitmap at all.
	
	Use Background Save and Background Print
	----------------------------------------
	
	Background Save:
	
	To continue working in Word while you save a document, turn on the background
	save option. Keep in mind that background save uses additional system memory; if
	you need to conserve system resources, you may want to turn off background save.
	To change the background save option:
	
	1. On the Tools menu, click Options, and then click the Save tab.
	
	2. Select or clear the Allow Background Saves check box.
	
	  NOTE: When Word saves a document in the background, a pulsing disk icon
	  appears on the status bar.
	
	  NOTE: If Word can't save a document in the background (for example, if you
	  don't have enough hard disk space or if you're saving a document to a floppy
	  disk), Word saves the document in the foreground instead.
	
	Background Printing:
	
	Select the Background Printing option that best fits the way you work. With
	Background Printing turned on, your document prints a bit more slowly, but you
	can continue working in Word while your document prints. With Background
	Printing turned off, your document prints quickly, but you cannot work in Word
	until the print job is finished. To change the Background Printing option, do
	the following:
	
	1. On the Tools menu, click Options, and then click the Print tab.
	
	2. Select or clear Background printing check box.
	
	Turn Off Background Spelling and Grammar Checking
	-------------------------------------------------
	
	Background spelling and grammar checking allows Word to show you misspellings
	(red wavy underlines) and grammatical errors (green wavy underlines) while you
	are typing. On some systems, this can cause your system to respond slower than
	normal. To turn off background spelling and grammar checking, follow these
	steps:
	
	1. On the Tools menu, click Options, and then click the Spelling & Grammar
	  tab.
	
	2. Clear the Check spelling as you type and Check grammar as you type check
	  boxes.
	
	Saving to Word 95 or 6.x
	------------------------
	
	You may find the need to save your Word 97 documents to Word 95 or 6.x format, so
	you can share documents with users of those versions of Word. In Word 97, you
	have the option to save the document using the Microsoft Word 6.0-95 converter.
	However, if you want to increase speed when dealing with Word 95 or 6.x
	documents, you may want to install the Microsoft Word 97 converter on the
	computer using Word 6.0 and 95. This way the conversion is done in Word 7.0 for
	Windows 95 or 6.x; this method of conversion may be faster than saving to Word
	6.x/95.
	
	To use the Word 97 converter after you install it, start Word 7.0 or Word 6.x,
	and then open a Word 97 document. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  
	
	  Q162214 WD: How to Obtain the Word 97-2000 Import Converter
	
	Change Your View and View Settings
	----------------------------------
	
	View:
	
	In Word, work in normal view instead of page layout view whenever possible. In
	page layout view, Word takes longer to redraw the screen and repaginate the
	document. To change to normal view, click Normal on the View menu.
	
	View Settings:
	
	Use Picture Placeholders if your document contains extensive graphics. This
	option displays a blank box in place of each graphic in your document. To change
	the Picture Placeholders option, follow these steps:
	
	1. On the Tools menu, click Options, and then click the View tab.
	
	2. Select or clear Picture Placeholders check box.
	
	Use the Draft Font option to speed up screen display in documents with extensive
	formatting and graphics. This option displays most character formatting as
	underlined and bold, graphics as empty boxes; this option is only available in
	normal view.
	
	To change the Draft Font option use the following steps:
	
	1. Switch to normal view (on the View menu, click Normal).
	
	2. On the Tools menu, click Options, and then click the View tab.
	
	3. Select the Draft font check box.
	
	Adjust Your System to Speed Up Printing
	---------------------------------------
	
	If you print large documents that take several minutes to print, disable any
	screen savers during the print job or switch to a blank screen saver.
	
	Animated screen savers use computer processor time that you can allocate to a
	print job. For more information, see your screen saver Control Panel program or
	documentation.
	
	Print using the Draft output option. This option prints the document with minimal
	formatting, which makes the document print faster (this option is ideal for
	printing proofs).
	
	NOTE: Some printers do not support this option.
	
	To change the Draft output option, follow these steps:
	
	1. On the Tools menu, click Options, and then click the Print tab.
	
	2. Select or clear Draft output check box.
	
	If you don't need to continue working while Word is printing, turn off the
	Background Printing option in Word.
	
	This option allocates processor time to Word during a print job so you can
	continue working while Word is printing; however, this means less processor time
	is available for printing. Select the Background Printing option that best fits
	the way you work. With Background Printing turned on, your document prints a bit
	more slowly, but you can continue working in Word while your document is
	printing. With Background Printing turned off, your document is printed quickly,
	but you cannot work in Word until the print job is finished. To turn off the
	Background Printing option, use the following steps:
	
	1. On the Tools menu, click Options, and then click the Print tab.
	
	2. Clear the Background printing check box.
	
	Turn Off Outlook Journaling
	---------------------------
	
	Outlook journaling tracks documents as they are closed or saved. On some
	computers, this may create a noticeable delay during the close or save process.
	Outlook journaling is turned on by default when Outlook is installed. To turn
	off Outlook journaling, follow these steps:
	
	1. Start Microsoft Outlook.
	
	2. In Outlook, on the Tools menu, click Options.
	
	3. Click the Journaling tab.
	
	4. Clear all of the check boxes in the dialog box.
	
	Turn Off the Mouse Scheme
	-------------------------
	
	Turning off the animated mouse scheme increases system performance, although the
	increase probably is not noticeable. To turn off the mouse scheme, follow these
	steps.
	
	1. On the Windows taskbar, click Start, point to Settings and click Control
	  Panel.
	
	2. Double-click Mouse.
	
	3. Click the Pointers tab.
	
	4. Set the Scheme to None.
	
	Increase Cache Size
	-------------------
	
	Increasing the cache size from the default amount of 64 kilobytes (KB) may allow
	you to check spelling and edit documents across a local area network.
	
	To use the RegOptions macro, follow these steps:
	
	1. On the Tools menu, click Templates and Add-Ins.
	
	2. Click Add. Select the following folder:
	
	  Program Files\Microsoft Office\Office\Macros
	
	3. Select the Support8 template (Support8.dot). Click OK twice.
	
	4. On the Tools menu, point to Macro, and then click Macros.
	
	5. Click to select the RegOptions macro, and then click Run.
	
	6. Click the Word 8.0 Options tab. Click to select CacheSize. In the Setting
	  box, type "1024" (without the quotation marks). Click OK.
	
	7. Quit and restart Word.
	
	GLOSSARY
	--------
	
	bitmap:
	
	A graphic made up of a collection of colored dots. The computer stores the
	graphic as one or more bits of information for each dot--hence the name bitmap.
	Some file name extensions for graphic files that are bitmaps include .pcx, .tif,
	.bmp, and .gif.
	
	compressed drive:
	
	A drive that has had its data compressed to take up less space. Special software
	must be running in the system to read from and write to a drive that is set up
	this way.
	
	conventional memory:
	
	The base RAM on your computer, typically the first 640K. Conventional memory is
	the only kind of RAM that MS-DOS-based applications can use, unless you use an
	expanded memory manager (EMM). Compare expanded memory, extended memory.
	
	driver (Windows printer or video driver):
	
	Software that Windows loads at startup. Drivers give Windows specific
	instructions about your video card and printer that Windows and Windows- based
	applications use to display information on the screen and to print information
	on your printer.
	
	expanded memory:
	
	A type of physical RAM, up to 8 MB, usually used by MS-DOS-based applications
	that support its use. Windows does not use expanded memory. In Windows, if you
	run an MS-DOS-based application (such as Microsoft Word 6.0 for MS-DOS) that
	requires expanded memory, Windows emulates expanded memory (if you are running
	in standard mode, Windows uses the EMM386.EXE device driver to emulate expanded
	memory). The use of expanded memory is defined by the Expanded Memory
	Specification (EMS). Compare conventional memory, extended memory.
	
	extended memory:
	
	Physical RAM beyond 1 MB, accessible when your computer is operating in protected
	mode (the mode that supports multitasking). Extended memory operates through a
	memory manager such as MS-DOS Himem.sys. Windows uses extended memory. Extended
	memory is not typically available to MS-DOS- based applications except through a
	device driver such as Emm386.exe. The use of extended memory is defined by the
	Extended Memory Specification (XMS). Compare expanded memory, conventional
	memory.
	
	pagination:
	
	The arrangement of a document's layout, specifically where page breaks fall
	within a given document.
	
	RAM:
	
	Acronym for random access memory. This is the memory on semiconductor chips in
	your computer, not on the hard disk. The more RAM you have, the more programs
	you can run at the same time and the faster your programs may run.
	
	swap file:
	
	A file Windows creates on your hard disk that it uses to swap information into
	and out of memory. Windows uses the swap file to create virtual memory.
	
	virtual memory:
	
	Also called disk memory. Virtual memory is not in the RAM chips. It is space on
	the hard disk that your computer uses as if it were RAM. With virtual memory,
	your applications can process files that would otherwise be too large to fit in
	physical RAM. Windows uses swap files to create virtual memory.
	
	ADDITIONAL RESOURCES
	--------------------
	
	www.microsoft.com on the World Wide Web:
	
	Check http://www.microsoft.com for additional information, tips, and tricks.
	
	Microsoft Windows 95 Resource Kit:
	
	The Microsoft Windows 95 Resource Kit has a chapter devoted to performance tuning
	that discusses topics such as the relation of performance to processor type,
	hard disk speed, memory (RAM), and conventional memory tuning. This chapter is a
	good resource for understanding the issues involved in configuring your PC for
	optimal performance. Other topics include Installation, Networking, Systems
	Management, Systems Configuration, Communications, Windows 95 Reference, Windows
	95 Appendixes, a Guided Tour for Administrators, and Resource Kit Utilities.
	
	  Microsoft Corporation
	  1348 pages with one CD
	  ISBN: 1-55615-678-2
	
	Microsoft Office 97 Resource Kit:
	
	Microsoft Office 97 Resource Kit is the definitive guide to installing,
	configuring, and supporting Office in your organization. Designed for system
	administrators, consultants, and power users, this guide offers complete
	coverage whether you're running Office in Windows 95 or Windows NT Workstation
	version 4.0.
	
	  Microsoft Corporation
	  1008 pages with one CD
	  ISBN: 1=57231=329=3
	
	Additional query words: configure optimize optimal set up enhance performance
	
	======================================================================
	Keywords          : word97 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
