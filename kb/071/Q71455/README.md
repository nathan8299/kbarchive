---
layout: page
title: "Q71455: HOWTO: Tracking Down Lost System Resources"
permalink: /kb/071/Q71455/
---

## Q71455: HOWTO: Tracking Down Lost System Resources

{% raw %}

	Article: Q71455
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly kbResource kbSDKPlatform
	Last Modified: 10-JUN-1999
	
	3.00 3.10
	WINDOWS
	kbprg
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The term "system resources" refers to two scarce system-wide resources: the USER
	heap and the GDI heap. These two segments are each limited to 64K, and they are
	both shared by all the applications running under Windows.
	
	During development of a Windows-based application, it is important to make sure
	that all the system resources allocated by the application at run time are
	released when the application terminates.
	
	If too many system resources are lost, and either the USER heap or the GDI heap
	gets too full, performance will degrade for the entire Windows system.
	
	The information below discusses how system resources can be "lost" by an
	application, and how to track down and correct such problems when they occur. In
	particular, it discusses:
	
	- Free System Resources -- A rough gauge of system resource use.
	
	- The GDI Heap -- The types of objects that are allocated in the GDI heap, and
	  general rules for making sure that these objects are properly released.
	
	- The USER Heap -- The types of objects that are allocated in the USER heap,
	  and general rules for making sure that these objects are properly released.
	
	- Troubleshooting and Heap Walker -- Specific techniques and tools for tracking
	  down lost system resources.
	
	MORE INFORMATION
	================
	
	Free System Resources
	---------------------
	
	The Program Manager's About Program Manager dialog box displays a Free System
	Resources value. This value indicates the amount of room left in the heap (USER
	or GDI) with the smallest amount of free space. There is no Windows API call
	that an application can use to obtain this value.
	
	The easiest way to tell if an application is losing system resources is to
	examine Program Manager's Free System Resources value before and after running
	the application. It is acceptable if this value goes down a little the first
	time the application is run, however if the value decreases every time the
	application runs and exits, system resources are being allocated and not
	released.
	
	The GDI Heap
	------------
	
	There are six GDI objects that a Windows program can create: pens, brushes,
	fonts, bitmaps, regions, and palettes. Space for each of these objects is
	allocated in the GDI heap.
	
	Normally, the life cycle of a GDI object requires that the following steps be
	performed:
	
	1. Create the GDI object.
	
	2. Use the object.
	
	3. Delete the object.
	
	The DeleteObject call is used to delete most GDI objects.
	
	The three general rules for deleting GDI objects are:
	
	- An application deletes all GDI objects that it creates.
	
	- Do not delete GDI objects while they are selected into a valid device
	  context.
	
	- Do not delete stock objects.
	
	Also, the following calls should always be matched:
	
	     CreateDC           -> DeleteDC
	     CreateCompatibleDC -> DeleteDC
	     CreateIC           -> DeleteDC
	     GetDC              -> ReleaseDC
	     BeginPaint         -> EndPaint
	
	Creating GDI objects that are never destroyed is probably the most common cause
	of lost system resources. A careful examination of every place in the
	application's code that uses GDI objects will often reveal the problem.
	
	The debugging version of Windows 3.1 will FatalExit when an application
	terminates if a GDI object owned by the application has not been deleted.
	
	The USER Heap
	-------------
	
	When an application creates window classes, windows, and menus, these objects
	take up room in the USER heap. When an application terminates, Windows usually
	reclaims the memory used by objects in the USER heap.
	
	Menus are a notable exception to this rule. Windows destroys the current menu of
	a window that is being destroyed. Windows does not destroy menus if they are not
	the current menu for any window. This can cause problems for applications that
	switch between multiple menus: the "extra" menus are not automatically destroyed
	when the application terminates.
	
	Therefore, if an application uses multiple menus, perform the following steps:
	
	1. Keep the handle to each menu.
	
	2. When the application is terminating, use the GetMenu function to discover
	  which menu is currently being used. Do not call the DestroyMenu function on
	  this menu, Windows will destroy it automatically.
	
	3. Call the DestroyMenu function to destroy each of the other menus. This will
	  reclaim the memory in the USER heap that these menus were using.
	
	Because the USER heap is a shared system resource, it is important that an
	application does not allocate too many USER objects at once. If the USER heap
	becomes too full, subsequent calls to the RegisterClass and CreateWindow
	functions will fail.
	
	This means that an application cannot create an excessively large number of
	windows. Also, when calling the RegisterClass functions, make sure that the
	cbWndExtra and cbClassExtra fields of the WNDCLASS structure are explicitly set
	to 0 (zero) if no extra bytes are needed.
	
	Also, the following calls should always be matched:
	
	     CreateIcon   -> DestroyIcon
	     CreateCursor -> DestroyCursor
	
	Troubleshooting and Heap Walker
	-------------------------------
	
	As mentioned above, Program Manager's Free Systems Resources value can provide
	evidence that memory objects are not being reclaimed in the USER or GDI heaps.
	
	It is sometimes unclear whether or not a particular Windows API call that creates
	an object must be balanced by a later call to explicitly delete the object. The
	following is a simple test that can be performed to find out:
	
	1. Alter the Generic sample application to ensure that it contains a loop that
	  makes the API call in question 50 times, creating 50 of the objects in
	  question.
	
	2. Run this version of Generic repeatedly. If the Program Manager's Free System
	  Resources value goes down every time Generic runs and exits, a balancing API
	  call must be made to reclaim the system resources before Generic terminates.
	
	The most powerful tool for looking at problems with lost system resources is the
	Heap Walker application. Heap Walker is included with the Microsoft Windows
	Software Development Kit (SDK). Chapter 11 of the "Microsoft Windows Software
	Development Kit Tools" guide explains how to use Heap Walker. In particular,
	page 11-8 outlines the procedure for checking for leftover GDI objects.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          : kb16bitonly kbResource kbSDKPlatform 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
