---
layout: page
title: "Q166725: SMS: How to Upgrade Windows NT Workstation 3.51 to 4.0 w/ SMS"
permalink: /kb/166/Q166725/
---

## Q166725: SMS: How to Upgrade Windows NT Workstation 3.51 to 4.0 w/ SMS

{% raw %}

	Article: Q166725
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.1,1.2,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbusage kbPCM smspcm
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes the steps involved for successfully upgrading a computer
	running Windows NT Workstation 3.51 to version 4.0 using both Systems Management
	Server versions 1.1 and 1.2.
	
	MORE INFORMATION
	================
	
	Step 1: Preparing the Required Files
	------------------------------------
	
	Sending Windows NT Workstation version 4.0 unattended upgrade jobs using Systems
	Management Server requires the following:
	
	1. A Windows NT Workstation package definition file (PDF), available at:
	
	   - On the Windows NT Workstation 4.0 compact disc in the platform directory
	     of your choice
	
	   - http://www.microsoft.com/SMSMGMT/pdfs.htm.
	
	2. An unattended setup script.
	
	   - Ntupgrad.scr is supplied in the Sms\Site.srv\Maincfg.box\mstest directory
	     of a Systems Management Server 1.2 installation. You must rename this file
	     to Ntupgrad.400.
	
	3. The Windows NT Workstation setup wrapper files.
	
	  For Systems Management Server 1.2, this is not a concern. Systems Management
	  Server 1.1 requires the updated Systems Management Server 1.2 wrapper file.
	  The wrapper files are operating system and platform specific, and are located
	  in the Sms\Site.srv\Maincfg.box\mstest directory. If you do not have access
	  to a Systems Management Server 1.2 compact disc, contact Microsoft Technical
	  Support.
	
	  Wrapper file names, operating systems, and hardware platforms are:
	
	   - Ntencap.exe: Windows NT Workstation on x86-compatible computers
	
	   - Ntencapa.exe: Windows NT Workstation on Digital Alpha computers
	
	   - Ntencapm.exe: Windows NT Workstation on MIPS computers
	
	4. The retail version of Windows NT Workstation 4.0.
	
	  You must use a fully licensed retail version of Windows NT Workstation 4.0. A
	  limited license, developer edition, or OEM version of Windows NT Workstation
	  will not work.
	
	Step 2: Preparing the Source Directory
	--------------------------------------
	
	It is possible to use the entire Windows NT Workstation compact disc as the
	source for the package, but it is not recommended. The compact disc contains all
	platform versions of Windows NT Workstation, as well as the debug symbols for
	each platform. Keep in mind that to distribute the package, Systems Management
	Server requires at least four times the amount of disk space as the source
	requires.
	
	1. Create a directory on the site server or any other computer running Windows
	  NT Workstation or Server on the network. Give the directory a name like
	  Ntw4.src.
	
	2. Share the directory.
	
	3. Copy and rename the Ntupgrad.scr file to Ntupgrd.400 to the newly created
	  directory (in this case, the Ntw4.src directory).
	
	4. Copy the appropriate version of NTENCAP to the Ntw4.src directory.
	
	5. Copy the Nt40.pdf file to the Sms\Primesite.srv\Import.src\Enu directory on
	  the site server.
	
	6. Insert the Windows NT Workstation 4.0 compact disc in an assessable CD-ROM
	  drive.
	
	7. From the root of the Windows NT Workstation 4.0 compact disc, copy the
	  Autorun.inf and Cdrom_w.40 files to the Ntw4.src directory.
	
	8. Copy the entire platform directory of your chose to the Ntw4.src directory
	  (for example, Ntw4.src\I386).
	
	Step 3: Create the Package
	--------------------------
	
	1. Start the Systems Management Server Administrator program.
	
	2. open the Packages window.
	
	3. On the File menu, click New.
	
	4. Click Import.
	
	5. Drill down to the site server's Primsite.srv\Import.src\Enu directory.
	
	6. Select the Windows NT Workstation 4.0 PDF.
	
	7. Click the Workstations button.
	
	8. Type in the UNC share name of the source file (for example,
	  \\Mango\Ntw4.src).
	
	9. Click Close and update the package at all sites.
	
	Step 4: Distribute the Package
	------------------------------
	
	1. Make sure that you have at least four times the size of the source directory
	  of available free space on the Systems Management Server installation drive
	  on the site server.
	
	2. Arrange the windows in the Systems Management Server Administrator program so
	  that you can see both the Packages window and the Sites window.
	
	3. In the Sites window, drill down to the domain that your target computer
	  belongs to.
	
	4. Drag the package from the package window and drop it on the target computer.
	  Doing this will bring up a Job Details dialog box.
	
	5. In the Job Details dialog box, make sure the package and job targets are
	  correct. Under the Run Phase, select "Automated Upgrade on <platform>"
	  (for example, "Automated Upgrade on x86" for a computer with an Intel
	  processor.)
	
	6. Set the Offer After, Mandatory, and Expires After dates.
	
	7. Click OK.
	
	8. Click OK in the Job Properties dialog box.
	
	Step 5: Run the Package
	-----------------------
	
	When the package appears in the workstation's Package Command Manager (PCM),
	click the Execute button.
	
	Troubleshooting
	---------------
	
	1. If the package fails to run correctly, check the Pcmwin32.log file and the
	  Ntencap.log file in the client's Ms\Sms\Logs directory.
	
	2. Try to manually connect to the SMS_PKG package source on the distribution
	  server, change to the appropriate package ID directory, and try to run the
	  command line from there.
	
	NOTE: There are several known issues with performing a Windows NT Server upgrade
	using the PCM service. These issues have been addressed in the PCM service
	update and is included in Systems Management Server 1.2 Service Pack 2. You can
	find information and updates for the PCM service at
	
	  http://microsoft.com/smsmgmt,
	
	and in the Microsoft Knowledge Base.
	
	
	Additional query words: ntw NTW4 prodsms
	
	======================================================================
	Keywords          : kbnetwork kbusage kbPCM smspcm 
	Technology        : kbSMSSearch kbSMS110 kbSMS120
	Version           : winnt:1.1,1.2,3.51,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
