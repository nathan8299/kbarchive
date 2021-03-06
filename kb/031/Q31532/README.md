---
layout: page
title: "Q31532: MASM 5.10 EXT.DOC: GetCursor - Returns Current Cursor Position"
permalink: /kb/031/Q31532/
---

## Q31532: MASM 5.10 EXT.DOC: GetCursor - Returns Current Cursor Position

{% raw %}

	Article: Q31532
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_masm
	Last Modified: 12-JAN-1989
	
	The following information is from the MASM Version 5.10 EXT.DOC
	file.
	   Please note that numbering for both COL and LINE variables begins
	with 0.
	
	/*  GetCursor - returns the current cursor position
	 *
	 *  The GetCursor function indicates current cursor position by
	 *  modifying the integers that px and py point to. The function
	 *  sets *px to the current cursor column, and *py to the current
	 *  cursor line.
	 *
	 *  px          Pointer to column-position variable
	 *  py          Pointer to line-position variable
	 */
	void pascal GetCursor (px, py);
	COL  far *px;
	LINE far *py;

{% endraw %}
