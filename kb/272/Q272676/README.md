---
layout: page
title: "Q272676: BUG: CComContainedObject::QueryInterface() Implementation Is Inc"
permalink: /kb/272/Q272676/
---

## Q272676: BUG: CComContainedObject::QueryInterface() Implementation Is Inc

{% raw %}

	Article: Q272676
	Product(s): Microsoft C Compiler
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbATL kbDSupport kbGrpDSMFCATL
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Active Template Library (ATL) 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are writing an aggregatable COM object in Active Template Library
	(ATL), unintended inner object interfaces could be exposed because of a bug in
	the implementation of the CComContainedObject::QueryInterface function.
	
	CAUSE
	=====
	
	The CComContainedObject::QueryInterface function calls the following lines in
	AtlCom.h:
	
	  	STDMETHOD(QueryInterface)(REFIID iid, void ** ppvObject)
	  	{
	  		HRESULT hr = OuterQueryInterface(iid, ppvObject);
	
	  		if (FAILED(hr) && _GetRawUnknown() != m_pOuterUnknown)
	  		 	hr = _InternalQueryInterface(iid, ppvObject);
	
	  		return hr;
	  	}
	
	If the OuterQueryInterface call fails, a "blind" _InternalQueryInterface is
	performed in the case of an aggregated object. This can cause a problem when,
	for instance, the outer object does not want to expose an interface of the inner
	object (and returns, E_FAIL, for example). The "blind" _InternalQueryInterface
	in the code returns that interface anyway.
	
	RESOLUTION
	==========
	
	To work around the problem and enable the aggregation to work correctly, comment
	out the highlighted lines in the AtlCom.h file:
	
	  	STDMETHOD(QueryInterface)(REFIID iid, void ** ppvObject)
	  	{
	  		HRESULT hr = OuterQueryInterface(iid, ppvObject);
	
	  		// Comment out the two lines below:
	  		// if (FAILED(hr) && _GetRawUnknown() != m_pOuterUnknown)
	  		// 	hr = _InternalQueryInterface(iid, ppvObject);
	
	  		return hr;
	  	}
	
	Make these modifications to a copy of the AtlCom.h file (for instance,
	FixAtlCom.h). Then, in the Stdafx.h file, comment out AtlCom.h and use
	FixAtlCom.h instead:
	
	      // #include <AtlCom.h>
	      #include "FixAtlCom.h" 
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	ATL uses CComContainedObject in the CComAggObject, CComPolyObject, and
	CComCachedTearOffObject classes. CComContainedObject implements IUnknown by
	delegating to the owner object's IUnknown. (The owner is either the outer object
	of an aggregation or the object for which a tear-off interface is being
	created.)
	
	To prevent unintended side effects and to allow the owner object to have full
	control, CComContainedObject must not independently return its own interfaces in
	response to a QueryInterface request, if the owner object's QueryInterface
	(called through OuterQueryInterface) does not work correctly.
	
	For example, assume that an inner object has an interface IID_Moo, which an outer
	object does not want to expose. The outer object could use a
	COM_INTERFACE_ENTRY_NOINTERFACE(IID_Moo) macro in its ATL COM map, right before
	a COM_INTERFACE_ENTRY_AGGREGATE_BLIND macro.
	
	The current ATL code for CComContainedObject::QueryInterface will allow a
	QueryInterface for IID_Moo to succeed, which is not expected behavior. The
	changes given here will allow for the IID_Moo QueryInterface call to fail, as
	expected.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q181265 HOWTO: Create ATL COM Objects
	
	View the following topics in the Microsoft Developer Network (MSDN) library:
	
	  CComContainedObject
	  http://msdn.microsoft.com/library/devprods/vs6/visualc/vcmfc/_atl_ccomcontainedobject.htm
	
	  CComAggObject
	  http://msdn.microsoft.com/library/devprods/vs6/visualc/vcmfc/_atl_ccomaggobject.htm
	
	  CComPolyObject
	  http://msdn.microsoft.com/library/devprods/vs6/visualc/vcmfc/_atl_ccompolyobject.htm
	
	  ATL Macros and Global Functions
	  http://msdn.microsoft.com/library/devprods/vs6/visualc/vcmfc/_atl_atl_macros_and_global_functions.htm
	
	Additional query words:
	
	======================================================================
	Keywords          : kbATL kbDSupport kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper kbATLsearch kbATL300
	Version           : :3.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
