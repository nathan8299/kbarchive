---
layout: page
title: "Q257707: FIX: Recordset Not Updated After Invoking the Move Method"
permalink: /kb/257/Q257707/
---

## Q257707: FIX: Recordset Not Updated After Invoking the Move Method

{% raw %}

	Article: Q257707
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbVBp kbVBp600bug kbDataEnv kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix kbATM
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a keyset cursor is being used in a multi-user DataEnvironment, the MoveNext
	and MovePrevious methods do not appear to update the recordset. If two users
	change a record, the changes that are made by the first user are not reflected
	in the second user's view of the data. This behavior occurs when the second user
	navigates to the updated record by using the MoveNext or MovePrevious methods.
	This behavior does not occur when the MoveFirst or MoveLast methods are used.
	
	CAUSE
	=====
	
	The records are being retrieved from the cache and do not reflect concurrent
	changes that other users have made to the source data.
	
	RESOLUTION
	==========
	
	Change the Cache Size setting of the Command object to 1. (The default value is
	100.)
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This bug was corrected in the latest
	service pack for Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the following
	article numbers to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	To download the latest Visual Studio service pack, visit the following Microsoft
	Web site:
	
	  http://msdn.microsoft.com/vstudio/downloads/updates.asp
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Data project. DataEnvironment1 and Connection1 are created by
	  default.
	
	2. Configure Connection1 to use OLE DB for SQL server.
	
	3. Click to select the server name and the Pubs database.
	
	4. Add a Command object to the connection.
	
	5. Specify SQL and enter "Select * from authors" (without the quotation marks)
	  in the SQL window.
	
	6. Locate the Advanced tab. Under Cursor Location, click to select Server-side,
	  under Cursor Type, click to select Keyset, and then under Lock Type, click to
	  select Optimistic.
	
	7. Drag the Command object to the frmDataEnv form (text boxes will be placed on
	  the form).
	
	8. Add four CommandButton controls to the form.
	
	9. Add the following code to the General Declarations section of Form1:
	
	  Private Sub Form_Load()
	      Command1.Caption = "Move Next"
	      Command2.Caption = "Move Previous"
	      Command3.Caption = "Move First"
	      Command4.Caption = "Move Last"
	  End Sub
	
	  Private Sub Command1_Click()
	      DataEnvironment1.rsCommand1.MoveNext
	  End Sub
	
	  Private Sub Command2_Click()
	      DataEnvironment1.rsCommand1.MovePrevious
	  End Sub
	
	  Private Sub Command3_Click()
	      DataEnvironment1.rsCommand1.MoveFirst
	  End Sub
	
	  Private Sub Command4_Click()
	      DataEnvironment1.rsCommand1.MoveLast
	  End Sub
	
	10. Save the project with two different names and run both projects, or create
	  an executable and run two instances of it.
	
	11. In the first instance, move to the second record and make a change to a
	  field. Click on Move Next to go to the third record.
	
	  In the second instance, click on Move Next to go to the second record and
	  note that the change is visible. This is as expected. Click on Move Previous
	  to move back to the first record.
	
	12. In the first instance, click on Move Previous to go to the second record and
	  make another change. Click on Move Next to go to the third record.
	
	  In the second instance, click on Move Next to go to the second record. Note
	  that the second change does not appear. Note also that subsequent changes to
	  any record do not appear. If you use MoveLast or MoveFirst, the records are
	  refreshed and the changes do appear.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbVBp kbVBp600bug kbDataEnv kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix kbATM 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
