---
layout: page
title: "Q68922: C 6.00 Library Source SETUP /copy May Fail for Some Files"
permalink: /kb/068/Q68922/
---

## Q68922: C 6.00 Library Source SETUP /copy May Fail for Some Files

{% raw %}

	Article: Q68922
	Product(s): See article
	Version(s): 6.00 6.00a | 6.00 6.00a
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 buglist6.00a | mspl13_c
	Last Modified: 6-FEB-1991
	
	The SETUP.EXE program provided with the Library Source for C versions
	6.00 and 6.00a has a switch called /copy that allows you to install
	single files from the install disk. SETUP will prompt for the file to
	be installed. If the file is not unique, the SETUP.EXE program will
	prompt for a path where it can find the file. However, SETUP will not
	allow long pathnames to be entered; therefore, the install will fail
	for most files.
	
	Because the files on the disk are compressed, the only way to correct
	the problem is to install all of the files.
	
	Microsoft has confirmed this to be a problem in the C Compiler Library
	Source SETUP.EXE version 6.00. We are researching this problem and
	will post new information here as it becomes available.

{% endraw %}
