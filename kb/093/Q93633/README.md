---
layout: page
title: "Q93633: HOWTO: How to Create or Modify a Database in an Application"
permalink: /kb/093/Q93633/
---

## Q93633: HOWTO: How to Create or Modify a Database in an Application

{% raw %}

	Article: Q93633
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:; WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 31-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows 
	- Microsoft FoxPro for MS-DOS 
	- Microsoft FoxBASE+ for MS-DOS 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In FoxPro 2.x, to create or modify a database under program control, you can use
	the COPY TO <name> STRUCTURE EXTENDED, the CREATE <name1> FROM
	<name2> command.
	
	In Visual FoxPro, you can use the ALTER TABLE command.
	
	Also, you can use the CREATE TABLE command in any version of FoxPro.
	
	MORE INFORMATION
	================
	
	The following code examples create a new database named TEMP that contains one
	field. The field is named LASTNAME and is 30 characters long.
	
	FoxPro 2.x
	----------
	
	     USE anyfile
	     COPY TO temp STRUCTURE EXTENDED
	     USE temp
	
	     APPEND BLANK
	     REPLACE field_name WITH 'lastname'
	     REPLACE field_len WITH 30
	     REPLACE field_type WITH 'C'
	     REPLACE field_dec WITH 0
	     CREATE newfile FROM temp
	
	NOTE: To add more than one field to the table, perform another APPEND BLANK and
	then the REPLACE sequence again.
	
	The COPY STRUCTURE EXTENDED command creates a new database file that describes
	the structure of the original database. Each record of the new database
	describes a field of the original database.
	
	NOTE: The COPY STRUCTURE EXTENDED and CREATE FROM commands also work in
	stand-alone applications created with the FoxPro Distribution Kit.
	
	Visual FoxPro
	-------------
	
	     USE anyfile
	     ALTER TABLE Temp  ADD COLUMN  "Lastname" C(10)
	
	CREATE TABLE Command
	--------------------
	
	You can also use the CREATE TABLE command to modify or create a database. Its
	syntax is as follows:
	
	     CREATE table <dbf_name>(<fname1> <type> [(<precision>[,
	  <scale>])[,
	        <fname2> ...]])
	
	The following example creates a table with the NAME, ADDR, CITY, ZIP, and SALARY
	fields, plus a memo field called COMMENTS:
	
	     CREATE Table employee ;
	        (name C(20), addr C(30), city C(30), zip C(5), salary N(8,2), ;
	           comments M)
	
	Additional query words: VFoxWin 3.00 FoxDos FoxWin 1.00 1.x 2.00 2.10 2.50 2.50a 2.50b 2.60 2.60a dbf
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxBASESearch kbVFP300
	Version           : MS-DOS:; WINDOWS:3.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
