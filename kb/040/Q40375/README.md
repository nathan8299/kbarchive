---
layout: page
title: "Q40375: Incomplete Memory Model Switch in User's Guide Example"
permalink: /kb/040/Q40375/
---

## Q40375: Incomplete Memory Model Switch in User's Guide Example

{% raw %}

	Article: Q40375
	Product(s): See article
	Version(s): 5.00 5.10 | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | docerr | mspl13_c
	Last Modified: 16-MAY-1989
	
	The following compile command line given on Page 158, Section 6.7, of
	the "Microsoft C 5.1 Optimizing Compiler User's Guide" is incorrect:
	
	   CL /As /Au /ND DATA1 PROG1.C
	
	This line should read as follows:
	
	   CL /AS /Au /ND DATA1 PROG1.C
	
	If a program is compiled with /As rather than /AS, the following error
	will be issued:
	
	   Command line error : D2013 incomplete model specification
	
	This error occurs because the data pointer size has not been
	specified.

{% endraw %}
