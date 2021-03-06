---
layout: page
title: "Q58640: &quot;7.0: Programmer's Guide&quot; Error Handling Example Correction"
permalink: /kb/058/Q58640/
---

## Q58640: &quot;7.0: Programmer's Guide&quot; Error Handling Example Correction

{% raw %}

	Article: Q58640
	Product(s): See article
	Version(s): 7.00 7.10 | 7.00 7.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | SR# S900207-56 docerr | mspl13_basic
	Last Modified: 8-JAN-1991
	
	The following are two corrections to the error handling example
	program on Page 291 of the "Microsoft BASIC 7.0: Programmer's Guide"
	(for 7.00 and 7.10):
	
	1. In Module #1, the line "ON ERROR GOTO Handler" should be removed
	   because there is no line label "Handler" in the first module.
	
	2. In Module #2, the line "DEFINT A-Z" should be added before the line
	   "Handler:". Since the default type for variables is SINGLE,
	   variables A and B would be incorrectly typed as SINGLE instead of
	   as INTEGER if the DEFINT A-Z line is not inserted.
	
	This information applies to Microsoft BASIC Professional Development
	System (PDS) versions 7.00 and 7.10 for MS-DOS and MS OS/2.

{% endraw %}
