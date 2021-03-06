---
layout: page
title: "Q193946: HOWTO: Demo of ADO AddNew, Update, Delete, Find and Filter"
permalink: /kb/193/Q193946/
---

## Q193946: HOWTO: Demo of ADO AddNew, Update, Delete, Find and Filter

{% raw %}

	Article: Q193946
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.1 SP2,2.5,2.6,6.0
	Operating System(s): 
	Keyword(s): kbActiveX kbCtrl kbDatabase kbMDAC kbSQL kbvfp600 kbGrpDSFox kbGrpDSMDAC kbDSupport kbA
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	- Microsoft Data Access Components versions 2.1 SP2, 2.5, 2.6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	ActiveX Data Objects (ADO) implements record manipulation commands analogous to
	those found in the native FoxPro language.
	
	The AddNew method adds a new, blank record to the end of the current Recordset.
	You use the Update method to write data to the Recordset. The Delete method
	removes the current record from the Recordset.
	
	The Find and Filter methods allow you to search the Recordset for specific field
	values. Both methods support compound expressions.
	
	MORE INFORMATION
	================
	
	The following example instantiates a Recordset from the AUTHORS table in the SQL
	Server PUBS sample database. The example demonstrates the AddNew and Update
	methods by adding a new record to the Recordset, uses the Find method to locate
	the new record and the Delete method to remove the new record. It then adds the
	same record again and uses the Filter property to locate and remove the record.
	
	NOTE: Substitute the SERVER, UID and PWD parameters appropriate to your SQL
	Server installation in the Recordset.Open method.
	
	In order to use this example, you must have Microsoft Data Access Components
	(MDAC) version 2.x or later installed, which is included in the data components
	of Visual Studio 6.0 or can be downloaded from the following Web address:
	
	  http://www.microsoft.com/data/
	
	Sample Code
	-----------
	
	  * Demonstrate the ADO AddNew, Update, Find,
	     * Filter and Delete functions.
	
	     #DEFINE adOpenDynamic 2
	     #DEFINE adLockOptimistic 3
	     oRecordSet = CREATEOBJECT("ADODB.Recordset")
	
	     * SQL Server driver defaults to server-side cursor,
	     * this would otherwise be necessary to use adOpenDynamic.
	     oRecordSet.OPEN("select * from authors", ;
	        "DRIVER={SQL Server};"+;
	        "SERVER=YourServerName;"+;
	        "DATABASE=pubs;"+;
	        "UID=YourUserName;"+;
	        "PWD=YourPassword",;
	        adOpenDynamic, adLockOptimistic)
	
	     =AddRec()
	     * Now the record is added - find it and delete it.
	     oRecordSet.FIND("au_id = '987-65-4321'")
	     IF NOT oRecordSet.EOF
	        oRecordSet.DELETE
	        =MESSAGEBOX("Record deleted")
	     ENDIF
	
	     * Remove comment to display the AU_IDs in the RecordSet.
	     * =ShowRS()
	
	     * Add it again, this time, use a compound Filter to find
	     * and delete it.
	     =AddRec()
	     oRecordSet.FILTER = ("au_id = '987-65-4321' and au_lname = 'Smith'")
	     IF NOT oRecordSet.EOF
	        oRecordSet.DELETE
	        =MESSAGEBOX("Record deleted")
	     ENDIF
	
	     * Remove comment to display the AU_IDs in the RecordSet
	     * =ShowRS()
	
	     * Remove the filter.
	     oRecordSet.FILTER = ""
	
	     * Function ShowRS:
	     * Display all the au_ids in the RecordSet.
	     FUNCTION ShowRs
	
	     CLEAR
	     oRecordSet.MoveFirst
	     ? oRecordSet.RecordCount
	     * print the au_id field values
	     DO WHILE ! oRecordSet.EOF
	        ?oRecordSet.FIELDS("au_id").VALUE
	     oRecordSet.MoveNext
	     ENDDO
	
	     * Function AddRec:
	     * Add a new record to the authors table.
	     FUNCTION AddRec
	
	     oRecordSet.AddNew
	     oRecordSet.FIELDS("au_id")= '987-65-4321'
	     oRecordSet.FIELDS("au_lname") = "Smith"
	     oRecordSet.FIELDS("au_fname") = "John"
	     oRecordSet.FIELDS("phone") = 9999999999
	     oRecordSet.FIELDS("address") = "123 4th Street"
	     oRecordSet.FIELDS("city") = "New York"
	     oRecordSet.FIELDS("state") = "NY"
	     oRecordSet.FIELDS("zip") = "99999"
	     oRecordSet.FIELDS("contract") = .T.
	     oRecordSet.UPDATE
	     =MESSAGEBOX("Record added")
	
	Additional query words: Update AddNew Find Filter Delete ADO Recordset kbVFp600 kbActiveX kbADO kbSQL kbCtrl kbMDAC
	
	======================================================================
	Keywords          : kbActiveX kbCtrl kbDatabase kbMDAC kbSQL kbvfp600 kbGrpDSFox kbGrpDSMDAC kbDSupport kbADO210sp2 kbMDAC210SP2 kbMDAC250 kbADO250 kbMDAC260 kbATM kbSQLProg 
	Technology        : kbVFPsearch kbAudDeveloper kbMDACSearch kbMDAC210SP2 kbMDAC250 kbMDAC260 kbVFP600
	Version           : WINDOWS:2.1 SP2,2.5,2.6,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
