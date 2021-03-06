---
layout: page
title: "Q150312: HOWTO: Install an ISAPI Filter Dynamic-Link Library"
permalink: /kb/150/Q150312/
---

## Q150312: HOWTO: Install an ISAPI Filter Dynamic-Link Library

{% raw %}

	Article: Q150312
	Product(s): Internet Information Server
	Version(s): 1.0,2.0,3.0,4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 25-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 1.0, 2.0, 3.0, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	ISAPI filters can be used with Internet Information Server to add features such
	as monitoring HTTP transactions or authentication. Filters can be loaded when
	the W3SVC service starts if they are added to a special key in the registry for
	IIS 1.0 through IIS 3.0, or in the metabase for IIS 4.0 and IIS 5.0.
	
	MORE INFORMATION
	================
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	IIS 1.0 - IIS 3.0
	
	To install an ISAPI filter for use with a Microsoft Internet Server, follow these
	steps:
	
	1. Copy the filter DLL to an appropriate subfolder, such as the SCRIPTS or
	  CGI-BIN subfolder.
	
	2. Run Regedt32.exe.
	
	3. Add the full path of the filter DLL to
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W3SVC\ Parameters\Filter
	  DLLs
	
	IIS 4.0 - IIS 5.0
	
	To install an ISAPI filter for use with a Microsoft Internet Information Server
	version 4.0 or 5.0, follow these steps:
	
	1. Copy the filter DLL to an appropriate folder, such as the SCRIPTS or CGI-BIN
	  subdirectory.
	
	2. Open the Internet Service Manager (MMC).
	
	3. Select the appropriate level for the ISAPI filter:
	
	4. 
	   - To use the ISAPI filter with all Web sites, select the ServerName icon.
	
	   - To use the ISAPI filter with a specific Web site, select the icon for that
	     Web site (for example, the default Web site).
	
	5. Right-click the level (icon) that you selected.
	
	6. Click the ISAPI Filters tab.
	
	  NOTE: To configure an ISAPI filter for all Web sites, first click the Edit
	  button that is next to the Master Properties of the WWW Service.
	
	7. Click Add.
	
	8. Type a name for the ISAPI filter.
	
	9. Click Browse and select the ISAPI filter that you copied in step 1.
	
	10. Click OK.
	
	11. Stop the IISADMIN service. To do this, either type "net stop iisadmin /y"
	  (without the quotation marks) at a command prompt, or use the Services
	  applet that is located in Control Panel (in Windows NT 4.0) or
	  Administrative Tools (in Windows 2000).
	
	12. Start the World Wide Web Publishing Service by typing "net start w3svc"
	  (without the quotation marks) at a command prompt, or by using the Services
	  applet that is located in Control Panel (in Windows NT 4.0) or
	  Administrative Tools (in Windows 2000).
	
	13. Repeat the previous step for any other services that were stopped in step
	  11.
	
	14. Browse back to the ISAPI Filters tab (by following steps 1-5) and verify
	  that the filter is loaded properly. You should see a green arrow that is
	  pointing up under the Status column.
	
	NOTE: The ISAPI Filters tab specifies a load order, with the filter at the top of
	the list loading first. Normally Sspifilt.dll, the ISAPI filter for SSL, is at
	the top of the list to allow any other filters to access data before IIS
	encrypts and transmits or decrypts and receives TTPS traffic.
	
	Additional query words: prodiis CGI BGI
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbiisSearch kbiis500 kbiis400 kbiis300 kbiis200 kbiis100
	Version           : :1.0,2.0,3.0,4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
