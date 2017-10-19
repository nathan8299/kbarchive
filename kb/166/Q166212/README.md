---
layout: page
title: "Q166212: INFO: ProcessMessageFilter gets called only for messages posted"
permalink: kb/166/Q166212/
---

## Q166212: INFO: ProcessMessageFilter gets called only for messages posted

	Article: Q166212
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.0,2.1,2.2,4.0,4.0a,4.1,4.2,4.2b,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbnokeyword kbHook kbMFC kbVC kbVC152 kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kb
	Last Modified: 04-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, version 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 2.0, 2.1, 2.2, 4.0, 4.0a, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2b 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2b 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	ProcessMessageFilter is only called for messages that are posted to the message
	queue and is not called for messages that are send directly to the window
	procedure. Therefore, this function cannot be used to monitor messages that are
	sent (by "Windows" or by the user) to a dialog box, message box, menu, or a
	scroll bar.
	
	ProcessMessageFilter is called from _AfxMsgFilterHook, which is the MFC hook
	procedure for WH_MSGFILTER hook. This hook procedure will be called by the
	system after a message generated by an input event (in a dialog box, message
	box, menu, or scroll bar) is retrieved from the message queue. Since messages
	sent directly to the window procedure (by SendMessage) do not go through the
	message queue, this hook procedure is not called by Windows. This in turn blocks
	the call to ProcessMessageFilter.
	
	MORE INFORMATION
	================
	
	The WH_MSGFILTER hook is a task-specific hook that enables an application to
	monitor messages passed to a menu, scroll bar, message box, or dialog box
	created by the application that installed the hook procedure. In a typical MFC
	application the WH_MSGFILTER is set in the global function AfxWinInit(), and in
	_AfxThreadEntry for multithreaded applications, with _AfxMsgFilterHook as the
	callback or the hook procedure.
	
	The callback function for this hook is called after these messages are retrieved
	from the queue, just before dispatching them, performing special processing as
	appropriate. Since messages sent directly to the window procedure (by
	SendMessage) do not go through the message queue, the hook procedure
	(_AfxMsgFilterHook) is not called by Windows.
	
	ProcessMessageFilter of CWinThread (in MFC 3.x and up) and CWinApp (in MFC 2.x)
	is called from the _AfxMsgFilterHook hook procedure. Since the hook procedure
	will not be called for messages sent directly to the window procedure,
	ProcessMessageFilter will not get called and none of the special code inside
	will execute.
	
	In general, all the keyboard and mouse messages, along with the WM_PAINT and
	WM_TIMER messages, are posted to the message queue. ProcessMessageFilter will
	not be called for messages like WM_SETFOCUS, WM_KILLFOCUS, WM_SETCURSOR,
	WM_COMMAND, WM_CTLCOLOR, WM_ACTIVATE, etc., since these are sent directly to the
	window procedure.
	
	To monitor messages that are sent to a menu, message box, dialog box or a scroll
	bar, set a WH_CALLWNDPROC hook. This hook is called whenever a message is sent
	directly to a window procedure. Note that there will be a tradeoff with
	performance since this hook procedure is called for every message that are sent
	through SendMessage.
	
	REFERENCES
	==========
	
	Additional information on SetWindowsHookEx, MessageProc, WH_MSGFILTER can be
	found in the Windows API documentation.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbnokeyword kbHook kbMFC kbVC kbVC152 kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC420 kbVC500 kbVC600 kbVS600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:2.0,2.1,2.2,4.0,4.0a,4.1,4.2,4.2b,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	