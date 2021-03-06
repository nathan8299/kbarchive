---
layout: page
title: "Q108305: INFO: Handling an Existing Call on a Line"
permalink: /kb/108/Q108305/
---

## Q108305: INFO: Handling an Existing Call on a Line

{% raw %}

	Article: Q108305
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1,95; winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	- Microsoft Win32 Application Programming Interface (API) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Windows Telephony application programming interface (TAPI) provides a way
	for a TAPI application to handle calls that are initially unknown to the
	application and/or the Telephony service provider via the
	LINECALLPARAMFLAGS_IDLE flag when invoking lineMakeCall. In an analog telephone
	environment, lineGetNewCalls can't provide this functionality for reasons
	explained below.
	
	MORE INFORMATION
	================
	
	A user might manually place a call on a telephone, and then start up his or her
	computer to send or receive a fax on the same call. A TAPI application has to
	invoke lineMakeCall to create a call appearance. Normally, an implementation of
	lineMakeCall checks to see if the line is already in use before it places the
	call. In an implementation through a modem (such as the sample service provider
	supplied with the TAPI SDK: ATSP), the service provider does this normally by
	going off-hook and listening for a dial tone. However, if the application is
	breaking into a call that already exists on a line, the service provider does
	not want to listen for the dial tone first--it won't hear it. Additionally, the
	service provider shouldn't return LINEERR_CALLUNAVAIL because the line is in
	use.
	
	To handle this situation, TAPI provides the LINECALLPARAMFLAGS_IDLE flag. If the
	application wants to break into an existing call on the line (not a call known
	to TAPI but a call that TAPI was not previously aware of), then it will turn off
	the _IDLE bit. Conversely, if the application wants the provider to start with a
	"fresh" call (that is, a call with a dial tone), it will set the
	LINECALLPARAMFLAGS_IDLE bit.
	
	In the case of analog devices, the service provider and TAPI are unaware of the
	call until lineMakeCall is invoked--lineGetNewCalls cannot be used to get a
	handle to the call; the call exists, but the software environment is not being
	synchronized with the "real" environment.
	
	In the digital PBX case, when TSPI_lineOpen is called, the service provider may
	be able to ask the hardware (phone or switch) about existing calls, and
	immediately establish these in TAPI by sending a LINE_NEWCALL message and a
	LINE_CALLSTATE message for each call, showing them as already being in the
	CONNECTED state; TAPI would give these calls to the highest-priority application
	with the specified media mode. There would be no need to call lineMakeCall to
	create a handle to the call, because the provider could do it spontaneously.
	
	Additional query words: 2.00 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWin32sSearch kbWin32API kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1,95; winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
