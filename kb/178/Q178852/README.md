---
layout: page
title: "Q178852: INFO: OLE DB Provider for ODBC Now an ODBC 3.5 and Higher Core C"
permalink: /kb/178/Q178852/
---

## Q178852: INFO: OLE DB Provider for ODBC Now an ODBC 3.5 and Higher Core C

{% raw %}

	Article: Q178852
	Product(s): Open Database Connectivity (ODBC)
	Version(s): WINDOWS:1.5,2.0,2.1,2.5,3.5,3.51
	Operating System(s): 
	Keyword(s): kbDatabase kbDriver kbMDAC kbODBC kbOLEDB kbProvider kbGrpDSMDAC kbDSupport kbMDAC210SP
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Open Database Connectivity, versions 3.5, 3.51 
	- Microsoft OLE DB, versions 1.5, 2.0, 2.1, 2.5 
	- Microsoft Data Access Components version 2.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With the release of ODBC 3.5, the OLE DB Provider for ODBC is now a required
	core component of ODBC.
	
	MORE INFORMATION
	================
	
	OLE DB provides support for both traditional relational data sources and
	non-relational data stores. OLE DB implicitly uses UNICODE strings. With version
	3.5, ODBC now offers UNICODE support.
	
	The 1.1 version of the OLE DB Provider for ODBC was written to specific UNICODE
	specifications within ODBC 3.0. Because these specifications have changed in
	ODBC 3.5, you must have version 1.5 of the OLE DB Provider for ODBC when using
	ODBC 3.5. The OLE DB Provider for ODBC version in later releases should match
	the MDAC release they shipped with, for example, 2.1 with MDAC 2.1. The OLE DB
	Provider for ODBC should not be changed from the version which shipped with it's
	parent MDAC package, since the entire package is tested as a suite, and
	mismatched components may cause unpredictable behavior.
	
	
	If you install or redistribute ODBC 3.5 onto a computer with OLE DB 1.1 and ODBC
	3.0, you will have problems with any OLE DB application on that computer that
	uses the OLE DB Provider for ODBC, unless you also install the OLE DB Provider
	for ODBC, version 1.5. Version 1.1 of the ODBC Provider will not work with ODBC
	3.5 because it relies on ODBC 3.0 code that is no longer present in ODBC 3.5.
	
	While applications based on ODBC 3.5 can run without the presence of the OLE DB
	Provider for ODBC, distributing ODBC 3.5 without including the provider means
	installation of your application could cause problems with pre-existing
	OLE-DB-based applications that use that provider.
	
	This article deals with redistribution of Microsoft Data Access Components
	(MDAC), which includes ODBC, OLE DB, ADO, RDS, the MDAC Standalone, MDAC
	Redistribution and the Data Access SDK. The "Redistributing Microsoft Data
	Access Components" whitepaper presents a comprehensive overview of this subject,
	including referencing the content in this article. This whitepaper is located
	at:
	
	  http://msdn.microsoft.com/library/techart/msdn_redistmdac.htm
	
	Additional query words: ActiveX Data Object ADO objects
	
	======================================================================
	Keywords          : kbDatabase kbDriver kbMDAC kbODBC kbOLEDB kbProvider kbGrpDSMDAC kbDSupport kbMDAC210SP2 kbMDAC250 
	Technology        : kbAudDeveloper kbODBCSearch kbOLEDBSearch kbMDACSearch kbMDAC250 kbOLEDB150 kbOLEDB200 kbOLEDB210 kbOLEDB250 kbODBC350 kbODBC351
	Version           : WINDOWS:1.5,2.0,2.1,2.5,3.5,3.51
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
