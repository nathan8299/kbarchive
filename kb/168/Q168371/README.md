---
layout: page
title: "Q168371: HOWTO: IObjectSafety Marks ATL Controls Safe for Initializing"
permalink: /kb/168/Q168371/
---

## Q168371: HOWTO: IObjectSafety Marks ATL Controls Safe for Initializing

{% raw %}

	Article: Q168371
	Product(s): Microsoft C Compiler
	Version(s): 2.0,2.1,3.0
	Operating System(s): 
	Keyword(s): kbole kbActiveX kbATL200 kbATL210 kbCOMt kbCtrl kbInprocSvr kbMFC kbSDKInet kbVC500 kbG
	Last Modified: 07-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Active Template Library (ATL), versions 2.0, 2.1, 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can use the default implementation of IObjectSafetyImpl to mark a control as
	safe for scripting. In many cases, you will also want to mark the control as
	safe for initialization.
	
	NOTE: Only mark your control as safe for scripting or initialization if it really
	is safe. If the control is potentially unsafe and it is marked as safe, you may
	be held liable for damages. See the REFERENCES section below for more
	information.
	
	MORE INFORMATION
	================
	
	The steps you need to take to get the desired functionality involve using
	IObjectSafetyImpl as one of the classes that your control derives from and
	overriding GetInterfaceSafetyOptions and SetInterfaceSafetyOptions. This allows
	you to implement the desired functionality, which in this case means marking the
	control as safe for scripting and initialization.
	
	To use IObjectSafetyImpl, you need to add it to the list of classes your control
	is derived from. For example, in the Polygon tutorial you see the following:
	
	  class ATL_NO_VTABLE CPolyCtl :
	  ...
	     public IObjectSafetyImpl<CPolyCtl> // ATL's version of
	                                       // IObjectSafety
	  {
	  public:
	     BEGIN_COM_MAP(CPolyCtl)
	  ...
	        COM_INTERFACE_ENTRY_IMPL(IObjectSafety) // Tie IObjectSafety
	                                                // to this COM map
	     END_COM_MAP()
	
	  STDMETHOD(GetInterfaceSafetyOptions)(REFIID riid,
	                                    DWORD *pdwSupportedOptions,
	                                    DWORD *pdwEnabledOptions)
	  {
	  ATLTRACE(_T("CObjectSafetyImpl::GetInterfaceSafetyOptions\n"));
	  if (!pdwSupportedOptions || !pdwEnabledOptions)
	     return E_FAIL;
	  LPUNKNOWN pUnk;
	  if (_InternalQueryInterface (riid, (void**)&pUnk) == E_NOINTERFACE) {
	     // Our object doesn't even support this interface.
	     return E_NOINTERFACE;
	  }else{
	     // Cleanup after ourselves.
	     pUnk->Release();
	     pUnk = NULL;
	  }
	  if (riid == IID_IDispatch) {
	     // IDispatch is an interface used for scripting. If your
	     // control supports other IDispatch or Dual interfaces, you
	     // may decide to add them here as well. Client wants to know
	     // if object is safe for scripting. Only indicate safe for
	     // scripting when the interface is safe.
	     *pdwSupportedOptions = INTERFACESAFE_FOR_UNTRUSTED_CALLER;
	     *pdwEnabledOptions = m_dwSafety &
	                          INTERFACESAFE_FOR_UNTRUSTED_CALLER;
	     return S_OK;
	  }else if ((riid == IID_IPersistStreamInit) ||
	            (riid == IID_IPersistStorage)) {
	     // IID_IPersistStreamInit and IID_IPersistStorage are
	     // interfaces used for Initialization. If your control
	     // supports other Persistence interfaces, you may decide to
	     // add them here as well. Client wants to know if object is
	     // safe for initializing. Only indicate safe for initializing
	     // when the interface is safe.
	     *pdwSupportedOptions = INTERFACESAFE_FOR_UNTRUSTED_DATA;
	     *pdwEnabledOptions = m_dwSafety &
	                          INTERFACESAFE_FOR_UNTRUSTED_DATA;
	     return S_OK;
	  }else{
	     // We are saying that no other interfaces in this control are
	     // safe for initializing or scripting.
	     *pdwSupportedOptions = 0;
	     *pdwEnabledOptions = 0;
	     return E_FAIL;
	  }
	  }
	
	  STDMETHOD(SetInterfaceSafetyOptions)(REFIID riid,
	                                    DWORD dwOptionSetMask,
	                                    DWORD dwEnabledOptions)
	  {
	  ATLTRACE(_T("CObjectSafetyImpl::SetInterfaceSafetyOptions\n"));
	  if (!dwOptionSetMask && !dwEnabledOptions) return E_FAIL;
	  LPUNKNOWN pUnk;
	  if (_InternalQueryInterface (riid, (void**)&pUnk) == E_NOINTERFACE) {
	     // Our object doesn't even support this interface.
	     return E_NOINTERFACE;
	  }else{
	     // Cleanup after ourselves.
	     pUnk->Release();
	     pUnk = NULL;
	  }
	  // Store our current safety level to return in
	  // GetInterfaceSafetyOptions
	  m_dwSafety |= dwEnabledOptions & dwOptionSetMask;
	  if ((riid == IID_IDispatch) &&
	      (m_dwSafety & INTERFACESAFE_FOR_UNTRUSTED_CALLER)) {
	     // Client wants us to disable any functionality that would
	     // make the control unsafe for scripting. The same applies to
	     // any other IDispatch or Dual interfaces your control may
	     // support. Because our control is safe for scripting by
	     // default we just return S_OK.
	     return S_OK;
	  }else if (((riid == IID_IPersistStreamInit) ||
	             (riid == IID_IPersistStorage)) &&
	            (m_dwSafety & INTERFACESAFE_FOR_UNTRUSTED_DATA)) {
	     // Client wants us to make the control safe for initializing
	     // from persistent data. For these interfaces, this control
	     // is safe so we return S_OK. For Any interfaces that are not
	     // safe, we would return E_FAIL.
	     return S_OK;
	  }else{
	     // This control doesn't allow Initialization or Scripting
	     // from any other interfaces so return E_FAIL.
	     return E_FAIL;
	  }
	  }
	  ...
	  }
	
	In ATL 3.0, the implementation of IObjectSafetyImpl has changed so that you can
	now provide the safety options as a template parameter. For example, the
	declaration of the class above would appear as
	
	  class ATL_NO_VTABLE CPolyCtl :
	  ...
	     public IObjectSafetyImpl<CPolyCtl,
	        INTERFACESAFE_FOR_UNTRUSTED_CALLER |
	           INTERFACESAFE_FOR_UNTRUSTED_DATA>
	  {
	  public:
	     BEGIN_COM_MAP(CPolyCtl)
	  ...
	
	and you would not have to override the two methods. For additional information,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q192093 PRB: Compiler Errors When Porting IObjectSafetyImpl to ATL 3.0
	
	REFERENCES
	==========
	
	For additional information about marking ActiveX controls as safe for scripting
	and initialization, please see the following articles in the Microsoft Knowledge
	Base:
	
	  Q161873 HOWTO: Mark MFC Controls Safe for Scripting/Initialization
	
	  Q164119 SAMPLE: Implementing IObjectSafety in an ActiveX control
	
	For in-depth coverage on developing an ActiveX control and deploying it on the
	Web, see Paul Johns' article "The ABCs of MFC ActiveX Controls" at:
	
	  http://microsoft.com/intdev/controls/stoplite/
	
	For topics relevant to this discussion see his companion article "Signing and
	Marking ActiveX Controls" at:
	
	  http://microsoft.com/intdev/controls/signmark-f.htm
	
	(c) Microsoft Corporation 1997, All Rights Reserved. Contributions by Shawn W.
	Karr, Microsoft Corporation
	(c) Microsoft Corporation 1997, All Rights Reserved.
	Contributions by Shawn William Karr, Microsoft Corporation
	
	
	Additional query words: ATLIss ATLControl InetSDKSafeControl mfcole
	
	======================================================================
	Keywords          : kbole kbActiveX kbATL200 kbATL210 kbCOMt kbCtrl kbInprocSvr kbMFC kbSDKInet kbVC500 kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper kbATLsearch kbATL200 kbATL300 kbATL210
	Version           : :2.0,2.1,3.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
