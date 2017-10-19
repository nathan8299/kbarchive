---
layout: page
title: "Q130506: HOWTO: Use AERROR() in Place of DBERROR() for ODBC Errors"
permalink: kb/130/Q130506/
---

## Q130506: HOWTO: Use AERROR() in Place of DBERROR() for ODBC Errors

	Article: Q130506
	Product(s): Microsoft FoxPro
	Version(s): 2.5,3.0,5.0,6.0,7.0
	Operating System(s): 
	Keyword(s): kbvfp300 kbvfp600 kbMDAC250
	Last Modified: 10-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0, 7.0 
	- Microsoft Data Access Components version 2.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	DBERROR() is no longer used to retrieve errors generated by an ODBC function.
	
	AERROR() is a general Visual FoxPro error function that creates a memory variable
	array containing information about the most recent Visual FoxPro, OLE, or ODBC
	error.
	
	MORE INFORMATION
	================
	
	The following example shows how to use AERROR(). Here a database is specified in
	the ODBC function SQLEXEC() that does not exist on the server.
	
	     nHandle=SQLCONNECT('<SQL Server data source>','sa','')
	     nSuccess=SQLEXEC(nHandle,'use bad_db')
	     Dimension aErrArray[1]
	     nNumerrors=AERROR(aErrArray)
	
	The variable nNumerrors now contains the number of rows in the array aErrArray (2
	in this case) and the array aErrArray contains the error information, as shown
	below:
	
	  AERRARRAY   Pub  A
	  (1,1)            N    1526    (           1526.00000000)
	  (1,2)            C    "Connectivity error: [Microsoft][ODBC SQL Server
	                             Driver][SQL Server] Attempt to locate entry in
	                             Sysdatabases for database 'bad_db' by name
	                             failed - no entry found under that name. Make
	                             sure that name is entered properly."
	  (1,3)            C    "[Microsoft][ODBC SQL Server Driver][SQL Server]
	                             Attempt to locate entry in Sysdatabases for
	                             database 'bad_db' by name failed - no entry
	                             found under that name. Make sure that name is
	                             entered properly."
	  (1,4)            C    "08004"
	  (1,5)            N    911      (            911.00000000)
	  (1,6)            N    1        (              1.00000000)
	  (1,7)            C    .NULL.
	  (2,1)            N    1526     (           1526.00000000)
	  (2,2)            C    "Connectivity error: [Microsoft][ODBC SQL Server
	                             Driver][SQL Server] Attempt to locate entry in
	                             Sysdatabases for database 'bad_db' by name
	                             failed - no entry found under that name. Make
	                             sure that name is entered properly."
	  (2,3)            C    "[Microsoft][ODBC SQL Server Driver][SQL Server]
	                             Changed database context to 'pubs'."
	  (2,4)            C    "01000"
	  (2,5)            N    5701     (           5701.00000000)
	  (2,6)            N    1        (              1.00000000)
	  (2,7)            C    .NULL.
	
	The following table describes the contents of each element when an ODBC error
	numbered 1526 occurs. The array contains two or more rows; one row for each ODBC
	error.
	
	Element number  Description
	---------------------------
	
	    1          Numeric. Contains 1526.
	    2          Character. The text of the error message.
	    3          Character. The text of the ODBC error message.
	    4          Character. The current ODBC SQL state.
	    5          Numeric. The error number from the ODBC data source.
	    6          Numeric. The ODBC connection handle.
	    7          The null value.
	
	Additional query words: kbfest VFoxWin
	
	======================================================================
	Keywords          : kbvfp300 kbvfp600 kbMDAC250 
	Technology        : kbVFPsearch kbAudDeveloper kbMDACSearch kbMDAC250 kbVFP300 kbVFP500 kbVFP600 kbVFP700
	Version           : :2.5,3.0,5.0,6.0,7.0
	Issue type        : kbhowto
	
	=============================================================================
	