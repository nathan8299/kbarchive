---
layout: page
title: "Q131371: Determining System Version from a Windows-Based Application"
permalink: /kb/131/Q131371/
---

## Q131371: Determining System Version from a Windows-Based Application

{% raw %}

	Article: Q131371
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 04-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To create a Windows-based application that takes advantage of the features of
	each platform, it is necessary to determine what operating system the
	application is currently running with.
	
	The GetVersion() function can be used to determine what operating system and
	version is currently being used. A 16-bit Windows-based application might be
	running with Microsoft MS-DOS/Microsoft Windows, Microsoft Windows NT
	Workstation, Microsoft Windows NT Server, or Microsoft Windows Windows on Win32
	(WOW) is the term given for the operating environment when running a 16-bit
	Windows-based application with Microsoft Windows NT Workstation or Microsoft
	Windows NT Server.
	
	MORE INFORMATION
	================
	
	According to the documentation, the return value of the GetVersion() function is
	a DWORD that specifies the major and minor version numbers. The following table
	shows the return values from the GetVersion() function when used with various
	operating environments:
	
	  Environment   LOWORD                 HIWORD
	  -------------------------------------------------------
	  Windows 3.x   Windows version        MS-DOS version
	  WFW           Windows version 3.1    MS-DOS version
	  WOW           Windows version 3.1    MS-DOS version 5.0
	  Windows 95    Windows version 3.95   MS-DOS version 7.0
	
	Microsoft Windows operating system version 3.1 and WOW can return the same
	results. Therefore, 16-bit Windows-based applications may want to use the
	GetWinFlags() function to determine whether the application is being run with
	Microsoft Windows or WOW. The GetWinFlags() function returns a WF_WINNT flag if
	the application is running with WOW.
	
	GetWinFlags() is an existing function that has been modified to detect other
	platforms. To test for Microsoft Windows NT, add the following flag to your
	header file and use it to perform the test:
	
	     #define WF_WINNT         0x4000
	
	The following sample code can be used to test the values returned by the
	GetVersion() function.
	
	Sample Code
	-----------
	
	  #include <windows.h>
	
	  void main()
	  {
	
	     DWORD dwVersion;
	     char szVersion[80];
	
	     dwVersion = GetVersion();
	
	     wsprintf (szVersion, "Microsoft Windows %u.%u - MS-DOS %u.%u",
	              (LOBYTE(LOWORD(dwVersion))),
	              (HIBYTE(LOWORD(dwVersion))),
	              (HIBYTE(HIWORD(dwVersion))),
	              (LOBYTE(HIWORD(dwVersion))));
	
	     MessageBox( NULL, szVersion, "Version Check", MB_OK );
	  }
	
	If you want to be able to distinguish between Windows and Windows for Workgroups,
	use the following test.
	
	Sample Code
	-----------
	
	     #define WNNC_NET_MultiNet           0x8000
	     #define WNNC_SUBNET_WinWorkgroups   0x0004
	     #define WNNC_NET_TYPE               0x0002
	
	     HINSTANCE hModInst      = NULL;
	     FARPROC   lpWNetGetCaps = NULL;
	     WORD      wNetType;
	
	     hModInst = LoadLibrary( "USER.EXE" );
	     if( !(lpWNetGetCaps = GetProcAddress( hModInst, (LPSTR)"WNetGetCaps")) )
	        MessageBox (hWnd, "WNetGetCaps Not Found", NULL, MB_OK);
	     else
	     {
	     // Get the network type
	        wNetType = (*lpWNetGetCaps) (WNNC_NET_TYPE);
	        if( wNetType & WNNC_NET_MultiNet )
	        {
	        // a multinet driver is installed
	           if( LOBYTE(wNetType) & WNNC_SUBNET_WinWorkgroups )
	           // It is WFW
	              MessageBox( hWnd, "Windows for Workgroups", NULL, MB_OK);
	           else
	           // It is not WFW
	              MessageBox( hWnd, "Not Windows for Workgroups", NULL, MB_OK);
	        }
	     }
	
	     // Clean up the module instance
	     if( hModInst )
	        FreeLibrary( hModInst );
	
	Additional query words: 3.10 detect
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
