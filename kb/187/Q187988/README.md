---
layout: page
title: "Q187988: PRB: ActiveX Control Is Parent Window of Modeless Dialog"
permalink: /kb/187/Q187988/
---

## Q187988: PRB: ActiveX Control Is Parent Window of Modeless Dialog

{% raw %}

	Article: Q187988
	Product(s): Microsoft C Compiler
	Version(s): 4.2,4.2b,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbole kbActiveX kbCOMt kbCtrl kbCtrlCreate kbDlg kbMFC kbVC420 kbVC500 kbVC600 k
	Last Modified: 27-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 4.2b, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 4.2b, 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an ActiveX control is the parent window of a modeless dialog box or
	propertysheet window, the TAB key, arrow keys, and accelerator keys don't work
	as expected. The TAB key doesn't move input focus from one control to another.
	Pressing the arrow keys or accelerator keys in the modeless dialog box or
	propertysheet window has no effect.
	
	CAUSE
	=====
	
	The problem is the ActiveX control doesn't own the message pump. The message
	pump is owned by the container application. Therefore, all the keystroke
	messages are taken by the container application and not dispatched to the
	modeless dialog box or propertysheet window.
	
	The problem does not occur with a modal dialog box/propertysheet window because
	the message pump is owned by the dialog box manager, and it takes care of
	handling all keystroke messages.
	
	RESOLUTION
	==========
	
	Install a Windows WH_GETMESSAGE hook for the modeless dialog box/propertysheet
	derived class to allow it to intercept keystrokes and handle accelerators.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The following sample shows a way to install the Windows message hook to a
	modeless CPropertySheet-derived class:
	
	Sample Code
	-----------
	
	     // Handle to the Windows Message hook. It can be a global variable or a
	     // member variable in your CPropertySheet-derived class.
	     HHOOK hHook = NULL;
	
	     // Hook procedure for WH_GETMESSAGE hook type.
	     LRESULT CALLBACK GetMessageProc(int nCode, WPARAM wParam, LPARAM lParam)
	     {
	        // Switch the module state for the correct handle to be used.
	        AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
	
	        // If this is a keystrokes message, translate it in controls'
	        // PreTranslateMessage().
	        LPMSG lpMsg = (LPMSG) lParam;
	        if( (nCode >= 0) &&
	           PM_REMOVE == wParam &&
	           (lpMsg->message >= WM_KEYFIRST && lpMsg->message <= WM_KEYLAST) &&
	           AfxGetApp()->PreTranslateMessage((LPMSG)lParam) )
	           {
	           // The value returned from this hookproc is ignored, and it cannot
	           // be used to tell Windows the message has been handled. To avoid
	           // further processing, convert the message to WM_NULL before
	           // returning.
	           lpMsg->message = WM_NULL;
	           lpMsg->lParam = 0L;
	           lpMsg->wParam = 0;
	           }
	
	        // Passes the hook information to the next hook procedure in
	        // the current hook chain.
	        return ::CallNextHookEx(hHook, nCode, wParam, lParam);
	     }
	
	     // Declare and define the following two functions:
	     BOOL CModelessPropertySheet::OnInitDialog()
	     {
	        CPropertySheet::OnInitDialog();
	
	        // Install the WH_GETMESSAGE hook function.
	        hHook = ::SetWindowsHookEx(
	           WH_GETMESSAGE,
	           GetMessageProc,
	           AfxGetInstanceHandle(),
	           GetCurrentThreadId());
	        ASSERT (hHook);
	
	        return TRUE;   // Return TRUE unless you set the focus to a control.
	                       // EXCEPTION: OCX Property Pages should return FALSE.
	
	     }
	
	     void CModelessPropertySheet::OnClose()
	     {
	        // Uninstall the WH_GETMESSAGE hook function.
	        VERIFY (::UnhookWindowsHookEx (hHook));
	
	        CPropertySheet::OnClose();
	
	     }
	
	Steps to Reproduce the Problem
	------------------------------
	
	1. Select the MFC ActiveX ControlWizard to create an ActiveX control. Accept all
	  the default settings.
	
	2. Display a modeless dialog box or propertysheet window when double-clicking
	  inside the control.
	
	RESULTS: When the modeless dialog box or propertysheet window is shown, pressing
	the TAB key or accelerator keys has no effect.
	
	REFERENCES
	==========
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Yeong-Kah
	Tam, Microsoft Corporation.
	
	
	Additional query words: ocx kbcodesam tabs hooks dll mfcdll
	
	======================================================================
	Keywords          : kbcode kbole kbActiveX kbCOMt kbCtrl kbCtrlCreate kbDlg kbMFC kbVC420 kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC kbVCNET
	Version           : :4.2,4.2b,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
