---
layout: page
title: "Q57932: Incorrect Message from &quot;searchall&quot; with Regular Expressions"
permalink: /kb/057/Q57932/
---

## Q57932: Incorrect Message from &quot;searchall&quot; with Regular Expressions

{% raw %}

	Article: Q57932
	Product(s): See article
	Version(s): 1.02   | 1.02
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | M MEP buglist1.02 | mspl13_basic
	Last Modified: 23-JAN-1990
	
	The Microsoft Editor searchall function (that is, SHIFT+F6) may return
	the following invalid error message when using regular expressions:
	
	   +'pattern' not found
	
	'pattern' is the actual regular expression for which the search was
	requested.
	
	In this situation, searchall still finds all occurrences of the search
	pattern correctly -- only the message is incorrect.

{% endraw %}
