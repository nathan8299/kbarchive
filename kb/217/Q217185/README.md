---
layout: page
title: "Q217185: FIX: IRowsetImpl::GetData() Does Not Handle Nulls Correctly"
permalink: /kb/217/Q217185/
---

## Q217185: FIX: IRowsetImpl::GetData() Does Not Handle Nulls Correctly

{% raw %}

	Article: Q217185
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbservicepack kbDatabase kbOLEDB kbProvider kbVC600bug kbVS600sp2 kbVS600SP1 kbVS600sp3
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an OLE DB Provider returns a DBSTATUS of DBSTATUS_S_ISNULL for a text field
	created using the ATL OLE DB Provider templates then the length of the field
	returned to the OLE DB consumer is not explicitly set to zero. This behavior
	follows the OLE DB specification, but can cause problems if an OLE DB consumer
	application utilizes the field length without checking the DBSTATUS of the
	column first. For example, a consumer application may assume that a non-zero
	field length means that the field is not NULL which is a common assumption when
	using text fields.
	
	
	CAUSE
	=====
	
	IRowsetImpl::GetData does not explicitly set the length for the column to zero
	if the DBSTATUS of the column is set to DBSTATUS_S_ISNULL.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3. For more information
	about Visual Studio service packs, please see the following articles in the
	Microsoft Knowledge Base:
	
	Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	When implementing an CRowsetImpl derived class using the ATL OLE DB Provider
	template class, you can override the GetDBStatus function to provide DBSTATUS
	information for each field returned by the OLE DB Provider. If you return
	DBSTATUS_S_ISNULL from the GetDBStatus function for a particular field, this
	indicates to the OLE DB consumer that the particular field is NULL.
	
	Internally, IRowsetImpl::GetData checks the DBSTATUS value you set for each field
	when returning the data to the consumer. If you set DBSTATUS to
	DBSTATUS_S_ISNULL, IRowsetImpl::GetData does not update the length indicator for
	a text field to 0. IRowsetImpl::GetData returns an unmodified length indicator
	to the client if you set the DBSTATUS of a field to DBSTATUS_S_ISNULL.
	
	Steps to reproduce
	------------------
	
	1. Create a new ATL OLE DB Provider named TESTPROV using the ATL OLE DB Provider
	  Wizard.
	
	2. Add a GetDBStatus method to the CTESTPROVRowset class as shown in the
	  following code sample:
	
	     class CTESTPROVRowset : public CRowsetImpl< CTESTPROVRowset,
	     CTESTPROVWindowsFile, CTESTPROVCommand>                               
	     {
	        public:
	           HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
	           {
	               // Etc....
	           }
	   //Add the following method      
	           DBSTATUS GetDBStatus( CSimpleRow* pRow , ATLCOLUMNINFO* pColInfo )
	           {
	              // Force column 4 (FileName) to null for every single row.
	              if ( 4 == pColInfo->iOrdinal )
	                 return DBSTATUS_S_ISNULL;
	              return DBSTATUS_S_OK;
	           }
	     };
	
	3. Build the project to create and register the TESTPROV OLE DB Provider DLL.
	
	4. Test the Provider using the following VB client code:
	
	     ' The following code requires a reference to Microsoft ActiveX Data
	     ' Objects library in your VB project in order to compile correctly.
	     Sub CheckTESTPROV()
	     Dim rs As New ADODB.recordset
	     Dim f As ADODB.Field
	     Dim strFieldStatus As String
	        rs.Open "c:\*.*", "Provider=TESTPROV OLE DB Provider;"
	        For Each f In rs.fields
	           If IsNull(f.Value) Then
	              strFieldStatus = "DBSTATUS_S_ISNULL"
	           Else
	              strFieldStatus = "DBSTATUS_S_OK"
	           End If
	           Debug.Print "[" & f.Name & "]"
	           Debug.Print "  Field Status = " & strFieldStatus
	           Debug.Print "  DefinedSize  = " & f.DefinedSize
	           Debug.Print "  ActualSize   = " & f.ActualSize
	        Next f
	     End Sub
	
	If the Provider correctly updates the length indicator to zero when
	DBSTATUS_S_ISNULL is encountered, the following output for the FileName field
	should appear in the debug window:
	
	  [FileName]
	    Field Status = DBSTATUS_S_ISNULL
	    DefinedSize  = 260
	    ActualSize   = 0
	
	If the Provider ignores the length indicator when DBSTATUS_S_ISNULL is
	encountered, then ActualSize will report some non-zero value.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbservicepack kbDatabase kbOLEDB kbProvider kbVC600bug kbVS600sp2 kbVS600SP1 kbVS600sp3fix kbGrpDSVCDB kbMDACNoSweep 
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch
	Version           : :6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
