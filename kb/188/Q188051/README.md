---
layout: page
title: "Q188051: SMS: Delmif.exe Syntax, Description, and Usage"
permalink: /kb/188/Q188051/
---

## Q188051: SMS: Delmif.exe Syntax, Description, and Usage

{% raw %}

	Article: Q188051
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Delmif.exe is a tool that is shipped with the BackOffice Resource Kit. The
	utility creates MIF that can delete clients both up and down a hierarchy. By
	default, DELMIF creates a delete-MIF file that deletes a client from a site
	database and all site databases above it.
	
	This file can be used in conjunction with a SQL trigger, so that DELMIF is
	invoked automatically after a client is deleted. DELMIF can also be used to
	delete clients down a hierarchy by creating command batch files and sending them
	to child sites as Package Command Manager service (PCMSVC) jobs.
	
	The problem occurs on the Alpha, MIPS, and x86 platforms.
	
	MORE INFORMATION
	================
	
	The following components can be used in the command line:
	
	  delmif SMSID [output_directory]
	
	  SMSID - The Systems Management Server ID of the client to delete.
	
	  SMSID_file - A file containing several SMSIDs to be deleted, one per line.
	
	  All characters after the first space on a line are ignored. An easy way to
	  create SMSID_file is to execute a query in the Systems Management Server
	  Administrator program (with Systems Management Server ID being the first
	  column in the query output), highlight the computer names, and paste them
	  into a Notepad file.
	
	  output_directory - The directory where the delete-MIF file is written. The
	  default is the LastLogonServerPath and ISVMIFCollectionPoint from C:\Sms.ini.
	  The output directory can be on any logon server in Logon.srv\Isvmif.box, or
	  on the site server in Site.srv\Isvmif.box. (The Site.srv directory gives a
	  slightly faster response). Specifying an output directory is recommended.
	
	Example
	-------
	
	The following command creates a delete-MIF file for the client with the SMS ID
	ABC00012:
	
	     delmif  ABC00012
	
	The following command creates a delete-MIF file for the client with the Systems
	Management Server ID ABC00345, and writes the delete-MIF file to D:\Test:
	
	     delmif  ABC00345  d:\test
	
	The following command creates a delete-MIF file for each client whose Systems
	Management Server ID is listed in Del.dat:
	
	     delmif  @del.dat
	
	Use the following syntax for a SQL trigger that will automate the execution of
	Delmif.exe when a computer's inventory is deleted from the Systems Management
	Server database. Because inventory MIFs flow up the Systems Management Server
	hierarchy, this will result in the same client inventory being deleted from all
	primary sites to the top of the Systems Management Server hierarchy.
	
	DELMIF trigger
	--------------
	
	     create trigger delmachine
	     on Machines
	     FOR DELETE
	     AS
	     DECLARE @smsid varchar(255)
	     DECLARE tIDs CURSOR FOR
	     select  SMSID0
	     from    MachineDataHistoryTable m (index = dwMachineID_idx),
	     Identification_SPEC i, deleted d
	     where   i.datakey = m.SpecificKey and
	             GroupKey = 1 and
	             m.ArchitectureKey = 5  and
	             m.dwMachineID = d.dwMachineID
	     open tIDs
	     FETCH NEXT
	     FROM tIDs
	     INTO @smsid
	     WHILE (@@fetch_status <> -1)
	     BEGIN
	        exec master..xp_delmif @smsid, "C:\SMS\site.srv\isvmif.box\"
	        FETCH NEXT
	        FROM tIDs
	        INTO @smsid
	     end
	     close tIDs
	     deallocate tIDs
	
	NOTE: It may be necessary to modify the output path the MIF is written to. For
	more information on this topic, refer to the Systems Management Server Resource
	Guide included in the BackOffice Resource Kit.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          :  
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
