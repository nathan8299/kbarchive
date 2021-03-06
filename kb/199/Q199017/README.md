---
layout: page
title: "Q199017: HOW TO: Deploy Visual Basic IIS Applications with the PDW"
permalink: /kb/199/Q199017/
---

## Q199017: HOW TO: Deploy Visual Basic IIS Applications with the PDW

{% raw %}

	Article: Q199017
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbDeployment kbVBp600 kbWebClasses kbGrpDSASP kbDSupport kbHOWTOmaster
	Last Modified: 30-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Internet Information Server version 4.0 
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Use the PDW to Create the Package
	- Deploy the Package to IIS
	- Deploy the Package to a Local or Network Folder
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This step-by-step article describes how to package and deploy Internet
	Information Server (IIS) applications by using the Microsoft Visual Basic
	Package and Deployment Wizard (PDW). The PDW packages your .dll file and its
	dependencies into a cabinet (.cab) file. The .cab file can then be deployed to a
	Web server where the files can be unpacked, installed, and registered.
	
	NOTE: HTML and Active Server Pages (ASP) pages are not packaged in the .cab file,
	but they are copied to the appropriate location when the application is
	deployed.
	
	Use the PDW to Create the Package
	---------------------------------
	
	To create a package for an IIS application, follow these steps:
	
	1. Load the application project file in Visual Basic, and then start the PDW
	  from the Add-Ins menu.
	
	NOTE: If the PDW is not on the Add-Ins menu, add it from the Add-In Manager,
	which is located on the Add-Ins menu.
	
	2. On the main PDW page, click to select Package.
	
	NOTE: You may receive the following message:
	
	  To proceed, the wizard requires the executable file '[project name].dll' for
	  this project. Click Browse to find the file or Compile to compile the
	  project.
	
	If the application has been recently compiled, click to select Browse to find the
	compiled .dll. Otherwise, click to select Compile.
	
	3. On the Package Type page, for IIS applications, click to select Internet
	  Package, and then click Next.
	
	4. On the Package Folder page, by default, the package is assembled in a
	  directory under the project directory named Package. If you want the package
	  to be placed in a different directory, type the file path in the Package
	  Folder text box, and then click Next. Otherwise, just click Next.
	
	5. The Included Files page lists all of the files that will be placed in the
	  .cab file. The default listed items are Mswcrun.dll (WebClass Runtime),
	  Visual Basic 6 Runtime, OLE Automation files, and your IIS application .dll
	  file. If you want any additional files added to the .cab, click Add, and then
	  locate the file to add. When you are finished, click Next to continue.
	
	  NOTE: You may experience problems when you deploy your package if you include
	  the WebClass Runtime, the Visual Basic Runtime, or the OLE Automation files.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q223499 PRB: Unexpected Error C0042116 with PDW 'Files Specified in Section
	  RInstallApplicationFiles of INF File filename.INF are Busy'
	
	6. Click Finish and the PDW completes the packaging of the IIS application. All
	  selected settings are stored in a script. If the package must be re-created
	  in the future, this script can be selected to automate the packaging process.
	
	Deploy the Package to IIS
	-------------------------
	
	After the application has been packaged, it can be deployed to a Web server. The
	Web server must have Posting Acceptor 2.0 installed for the PDW to function
	properly. For additional information about the Posting Acceptor, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q192116 HOWTO: Configure Posting Acceptor To Work With the PDW
	
	Additionally, IIS applications must be deployed to an existing virtual directory
	on the Web server.
	
	
	Follow these steps to deploy the package to the Web server:
	
	1. On the main PDW page, click to select Deploy.
	
	2. On the Package to Deploy page, click to select the package you want to
	  deploy, and then click Next. The package is referred to in the list box by
	  the script name that was selected in the last page of the packaging steps.
	
	3. On the Deployment Method page, click to select Web Publishing, and then click
	  Next. Packages can be published to a Web server or to local or network
	  folder.
	
	4. The Items to Deploy page prompts you for items to deploy to the Web server.
	  By default, this includes the cabinet package and any ASP, HTML, or other
	  files that are in the application project. Click to clear any files that you
	  do not want to deploy to the server, and then click Next.
	
	5. On the Additional Items to Deploy page, click to select any additional files
	  to be deployed that were not part of the project, and then click Next. Note
	  that these additional files must either be in the project directory or in one
	  of the subdirectories of the project directory.
	
	6. On the Web Publishing Site page, type the URL to where the package is to be
	  deployed. The package can be deployed by either HTTP Post or File Transfer
	  Protocol (FTP). For additional information about how to use FTP to deploy
	  Visual Basic Internet applications, click the article number below to view
	  the article in the Microsoft Knowledge Base:
	
	  Q192639 HOWTO: Use PDW to Deploy Using the FTP Web Publishing Method
	
	  NOTE: For a package to be deployed by HTTP Post, the Web server must be
	  configured with the Posting Acceptor 2.0. There is also an option here for
	  unpacking and installing the server-side .cab file. This option can only be
	  used with HTTP Post. Click Next to continue. You may receive the following
	  message:
	
	  The specified URL and publishing protocol can be saved in the registry as a
	  Web publishing site. This will verify that the URL and publishing protocol
	  are valid and will save time for future deployments to this site. Do you want
	  to store this information as a Web publishing site?
	
	Click Yes if you want to save this information in the registry. Otherwise, click
	No to continue.
	
	7. Click Finish and the PDW completes the deployment of your application.
	  Similar to when packaging applications, the selected settings are stored in a
	  script so that any future deployments for the current application can be
	  automated.
	
	Deploy the Package to a Local or Network Folder
	-----------------------------------------------
	
	Follow these steps to deploy the package to a local or network folder:
	
	1. On the main PDW page, click to select Deploy.
	
	2. For Package to Deploy, click to select the package that you want to deploy,
	  and then click Next. The package is referred to in the list box by the script
	  name that was selected in the last page of the packaging steps.
	
	3. For Deployment Method, click to select Folder, and then click Next. Packages
	  can be published to a Web server or to a local or network folder.
	
	4. For Folder, use the Browse button to locate the local or network folder in
	  which to deploy the application. When you are finished, click Next.
	
	5. Click Finish and the PDW completes deploying the application to the selected
	  folder. Selected settings are stored in a script so that future deployments
	  for the current application can be automated. Note that when you deploy the
	  package to a local or network folder, the package is not unpacked or
	  installed. The Package files are just copied to the selected location.
	
	REFERENCES
	==========
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q191039 HOWTO: Build an Internet Information Server Application
	
	  Q190166 PRB: PDW Does Not Include .ASP and .HTM Files for Standard Setup
	
	  Q242767 INFO: Deploying WebClasses with the Package and Deployment Wizard
	  (PDW)
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDeployment kbVBp600 kbWebClasses kbGrpDSASP kbDSupport kbHOWTOmaster 
	Technology        : kbVBSearch kbiisSearch kbAudDeveloper kbZNotKeyword6 kbiis500 kbiis400 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
