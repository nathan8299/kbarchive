---
layout: page
title: "Q171546: FIX: VB4 Apps with Unbound DBGrid Fail with VB5 DBGrid"
permalink: /kb/171/Q171546/
---

## Q171546: FIX: VB4 Apps with Unbound DBGrid Fail with VB5 DBGrid

{% raw %}

	Article: Q171546
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,97,97sp1
	Operating System(s): 
	Keyword(s): kbVBp400 kbVBp500 kbVS97sp2 kbVS97sp2fix kbGrpDSVBDB kb32bitOnly kbvbp500sp3fix
	Last Modified: 18-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using Visual Basic 4.0 with an Unbound DBGrid and the Visual Basic 5.0
	DBGrid32.ocx, data does not get cached correctly. This results in invalid rows
	being displayed in the grid.
	
	For example, an application using the Visual Basic 4.0 version would correctly
	display three rows of data. The same application would display only one row of
	data once the Visual Basic 5.0 version of the DBGrid control is installed.
	
	CAUSE
	=====
	
	This problem is caused by a bug in the Visual Basic 5.0 Data Bound Grid Controls
	(DBGrid32.ocx) in the version that ships with the product (5.00.3714) and in the
	version that ships with Visual Studio 97 Service Pack 1 (5.00.3817). Visual
	Studio 97 Service Pack 2 did not include an updated version of the control.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 3.
	
	For more information, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q170365 : INFO: Visual Studio 97 Service Packs - What, Where, and Why
	
	For a list of the Visual Basic 5.0 bugs that were fixed in the Visual Studio 97
	Service Pack 3, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q175450 : INFO: Visual Basic 5.0 Fixes in Visual Studio 97 Service Pack 3
	
	MORE INFORMATION
	================
	
	This problem does not occur if the application that uses the DBGrid control has
	been built with Visual Basic 5.0.
	
	This problem also does not occur if the application built by Visual Basic 4.0 is
	a 16-bit application. That application would use the 16-bit DBGrid control and
	would be unaffected by this problem in the 32-bit version of the control.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp400 kbVBp500 kbVS97sp2 kbVS97sp2fix kbGrpDSVBDB kb32bitOnly kbvbp500sp3fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVB500 kbVB400Search kbVB400 kbZNotKeyword3
	Version           : WINDOWS:4.0,5.0,97,97sp1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
