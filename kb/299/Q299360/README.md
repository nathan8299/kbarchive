---
layout: page
title: "Q299360: FP: Include Component, Shared Borders Incorrect on UNIX"
permalink: /kb/299/Q299360/
---

## Q299360: FP: Include Component, Shared Borders Incorrect on UNIX

{% raw %}

	Article: Q299360
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- SharePoint Team Services from Microsoft 
	- FrontPage 2002 Server Extensions from Microsoft 
	- Microsoft FrontPage 2002 
	- Microsoft FrontPage 2000 
	- Microsoft FrontPage 98 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you upgrade your UNIX-based site to the FrontPage 2002 Server Extensions,
	the shared borders and Include components do not appear correctly. The body of
	the main page appears as part of the shared border or the Include component,
	giving the appearance of duplicating data throughout the page.
	
	CAUSE
	=====
	
	This problem occurs if a performance tuning setting (such as the Max Cache
	Document Size setting) on the server is configured incorrectly. For information
	about how to configure performance tuning settings, see the "More Information"
	section later in this article.
	
	WORKAROUND
	==========
	
	To work around this problem, remove the configuration settings that affect the
	performance tuning options. To do this, follow these steps:
	
	Global Settings
	---------------
	
	IMPORTANT: Because these settings affect all sites on your server, follow these
	steps carefully.
	
	1. Log on to your UNIX server with root privileges.
	
	2. Open the following directory:
	
	  /usr/local/frontpage/version5.0
	
	3. In a text editor, open the Frontpage.cnf file.
	
	4. Locate the following lines and delete them:
	
	  CacheMaxDocMeta
	  CacheMaxImage
	  CacheMaxInclude
	  CacheMaxIncludeSize
	  CacheMinDocMeta
	
	5. Save and close the file. Quit the text editor program.
	
	6. Recalculate any affected Webs on the server.
	
	Site-Specific Settings
	----------------------
	
	For each site that continues to experience problems, follow these additional
	steps:
	
	1. Log on to your UNIX server with root privileges.
	
	2. Open the following directory:
	
	  /usr/local/frontpage
	
	  There should be at least one configuration file in this directory, although
	  there could be several. File names of configuration files on multihosted
	  systems have the following syntax:
	
	  my.host.name:PPP.cnf
	
	  where my.host.name is the fully qualified domain name of the server and PPP is
	  the port number of the Web server.
	
	  File names of configuration files on a single-host system have the following
	  syntax:
	
	  wePPP.cnf
	
	  where PPP is the port number of the Web server.
	
	3. In a text editor, open the file that corresponds to the affected Web server.
	
	4. Locate the following lines and delete them:
	
	  CacheMaxDocMeta
	  CacheMaxImage
	  CacheMaxInclude
	  CacheMaxIncludeSize
	  CacheMinDocMeta
	
	5. Save and close the file. Quit the text editor.
	
	6. Recalculate any affected Webs on the specific Web site.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	For more information about the performance tuning options and registry values
	used by the FrontPage 2002 Server Extensions, see the following Microsoft Web
	site:
	
	  http://www.microsoft.com/technet/sharepoint/admindoc/
	
	For additional information about this error and Microsoft Internet Information
	Services, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q298827 FP2002: Include Components, Shared Borders Incorrect on IIS
	
	
	Additional query words: front page STS SPTS FPSE
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch _IKkbbogus kbFrontPage2002 kbFrontPageServXSearch _IKkbZNotKeyword4 kbZNotKeyword2 kbFrontPage2000Search kbFrontPage2002Search kbFrontPage98Search kbZNotKeyword3 kbFrontPage2002ServX kbZNotKeyword5 kbSharePtTeamSvc
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
