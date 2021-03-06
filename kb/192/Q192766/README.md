---
layout: page
title: "Q192766: SAMPLE: ADSIBrow.exe Browses Active Directory w/ Visual FoxPro"
permalink: /kb/192/Q192766/
---

## Q192766: SAMPLE: ADSIBrow.exe Browses Active Directory w/ Visual FoxPro

{% raw %}

	Article: Q192766
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0; winnt:2.5
	Operating System(s): 
	Keyword(s): kbfile kbsample kbADSI kbAutomation kbCOMt kbvfp600 kbDSupport
	Last Modified: 12-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	ADSIBrow.exe is self-extracting executable file that contains the Visual FoxPro
	form files, ADSBrows.scx and ADSBrows.sct. The form ADSBrows is a sample form
	that demonstrates the navigation of an Active Directory Services (ADS) directory
	structure.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  ADSIBrow.exe
	
	Release Date: Sep-24-1998
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	ADSI is a Component Object Model (COM) based interface for accessing directory
	services. Each element of the network, such as users, printers and computers,
	can be treated as an object. The form ADSBrows demonstrates how to find an
	Active Directory Services (ADS) container object as well as the objects
	contained within that container.
	
	To use ADSBrows, run ADSIBrow.exe to extract the form files. Run the form from
	within Visual FoxPro by typing the following in the Command window:
	
	     DO FORM ADSBROWS
	
	In the ADS Path text box, change MyServer to a valid computer name for your
	network and click the Find button. If all of the Filters check boxes are clear,
	the browser displays all ADS objects for the computer name entered. The browser
	allows a user to drill down the object tree by clicking the plus sign to the
	left of an object.
	
	If any Filters check boxes are selected, the browser displays those objects that
	match the selected check boxes. In other words, if Users and Printers are
	checked, the browser displays the users and printers for the computer name
	entered.
	
	To view the properties for an object, select it in the Treeview list and click
	the Properties button. When the Properties button is clicked, the selected
	object's name, class, GUID and ADS path display.
	
	NOTE: In order to use the sample, you must install the Active Directory Service
	Interfaces. The Active Directory Service Interfaces can be installed from one of
	the following:
	
	- http://www.microsoft.com/windows/server/Technical/directory/
	- Microsoft Developer Network CD-ROM
	
	REFERENCES
	==========
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q190741 HOWTO: Get User Information Using ADSI
	
	  Q192300 HOWTO: Use ADSI for Printer Information and Control
	
	For more information on developing Web-based solutions for Internet Explorer,
	please see the following Web sites:
	
	  http://msdn.microsoft.com/workshop/default.asp
	
	  http://msdn.microsoft.com/ie/
	
	  http://support.microsoft.com/highlights/iep.asp?FR=0&SD=MSDN
	
	(c) Microsoft Corporation 1998, All Rights Reserved.
	Contributions by Mike A. Stewart, Microsoft Corporation
	
	
	Additional query words: ADSIBrow
	
	======================================================================
	Keywords          : kbfile kbsample kbADSI kbAutomation kbCOMt kbvfp600 kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0; winnt:2.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
