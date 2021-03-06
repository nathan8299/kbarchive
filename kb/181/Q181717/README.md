---
layout: page
title: "Q181717: FIX: Analyze Problems with Open Log Files"
permalink: /kb/181/Q181717/
---

## Q181717: FIX: Analyze Problems with Open Log Files

{% raw %}

	Article: Q181717
	Product(s): Microsoft SourceSafe
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbSSafe500bug kbSSafe500fix kbSSafe600fix
	Last Modified: 04-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Analyze reports returns the error listed below and if you are running Analyze
	with either the -f or the -d switch, or both, files are deleted either from the
	data\<a-z> directory, or destroyed in the SourceSafe database.
	
	Here is the error:
	
	  Unable to open file <physical filename>
	  File <physical filename> is already open.
	
	CAUSE
	=====
	
	If a log file (a file with no extension in one of the data\<a-z> folders)
	is opened and locked by a different process, such as a backup utility running
	simultaneously with Analyze, Analyze treats the file as an orphan.
	
	RESOLUTION
	==========
	
	The best cure is prevention. You should run Analyze without any switches before
	running it with either the -d switch or the -f switch. If Analyze reports that a
	file is already open, take whatever steps necessary to close that file before
	using the additional switches. Once the problem has occurred, the resolution
	will be determined by a number of factors, such as which files have been
	deleted, how important it is to maintain their history, and whether a file or
	project was affected. If you are not sure what action to take, contact Microsoft
	Technical Support.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in analyze version shipped with Visual
	SourceSafe 5.0.
	This bug was corrected in the version of analyze that ships with Visual
	SourceSafe 6.0 and the version of analyze that's available on the Web.
	Please see the REFERENCES section for more information about downloading the
	Analyze.exe file.
	
	MORE INFORMATION
	================
	
	An orphan file is one that has been destroyed from the SourceSafe database via
	the SourceSafe Explorer or the command line, and is not branched to or from a
	file that still exists in the database. In the scenario described in the CAUSE
	section, Analyze sees this file as an orphan, but its physical file pair still
	exists in the data\<a-z> folder. Analyze -d attempts to delete the file
	pair. It might delete either or both of the files, depending on which file is
	locked at the time it attempts the deletion. A locked file is not deleted. This
	may result in "File <physical data file name> not found" errors.
	
	Analyze -f behaves differently on projects and files as described below:
	
	- If the file pair represents a file, Analyze destroys the file in the
	  SourceSafe database. When this happens, the history of the parent project
	  shows that the file was destroyed by user "REBUILD". The physical file pair
	  of the file's parent project is copied to the Backup folder, in their
	  pre-analyzed state.
	
	- If the file pair represents a project, Analyze copies the corresponding file
	  pair to the backup directory, and attempts to delete the file pair.
	
	Analyze -d -f results in both situations described above.
	
	Steps to Reproduce Behavior
	---------------------------
	
	Note: Reproducing this behavior causes problems with the SourceSafe database. Do
	not attempt to reproduce this on a live database. Use this on a database that is
	set up for testing purposes only.
	
	Using an application that locks files that it opens, such as Microsoft Word,
	opens a log file in the SourceSafe data directory. Run Analyze with any
	combination of the -f and -d switches, for full information, use the -v4 switch.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q190881 SAMPLE: Analyze6.exe Utility for Visual SourceSafe
	
	  Q168634 INFO: When -d Switch of Analyze Deletes Files
	
	  Q167263 PRB: <filename> is Already Open
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe500bug kbSSafe500fix kbSSafe600fix 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe500
	Version           : :5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
