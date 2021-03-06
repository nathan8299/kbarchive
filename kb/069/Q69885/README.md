---
layout: page
title: "Q69885: DOC: SetBkColor() Does Not Support Dithered Colors"
permalink: /kb/069/Q69885/
---

## Q69885: DOC: SetBkColor() Does Not Support Dithered Colors

{% raw %}

	Article: Q69885
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1,95; winnt:3.5,3.51
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr kbOSWinNT350 kbOSWinNT351 kbOSWin95 kbSDKWin16
	Last Modified: 11-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	- Microsoft Win32 Application Programming Interface (API), used with:
	   - Microsoft Windows NT Server versions 3.5, 3.51 
	   - Microsoft Windows NT Workstation versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The syntax for the SetBkColor function is documented in the Microsoft Windows
	Software Development Kit (SDK) as follows:
	
	     DWORD SetBkColor(HDC hDC, COLORREF crColor);
	
	SetBkColor sets the current background color of the specified Device Context (DC)
	to the color that the crColor parameter references, or to the nearest physical
	color if the device cannot represent the RGB color value that the crColor
	parameter specifies. In other words, SetBkColor cannot be used to set the
	background to a dithered color and defaults to the physical color that is
	closest to the requested crColor value.
	
	MORE INFORMATION
	================
	
	This behavior can cause unexpected results for an application that changes the
	background color of a control to a color that cannot be represented by a color
	provided by the display device.
	
	Specifically, when an application specifies a dithered color for the background
	of an edit control, and specifies the same color for the text background,
	Windows paints the control in two distinct colors.
	
	For example, using the standard VGA display driver, the following call, in which
	COLOR_INACTIVEBORDER is a green/gray specified by RGB(64, 128, 128), sets the
	background color to gray (RGB(128, 128, 128)) rather than the dithered
	green/gray that is desired:
	
	     SetBkColor(wParam, GetSysColor(COLOR_INACTIVEBORDER));
	
	To illustrate, if the application uses the function call while processing the
	WM_CTLCOLOR message to change the color of an edit control, the window
	background is painted green/gray, and the text background defaults to the
	nearest physical color, which is gray. This produces a gray rectangle inside a
	green/gray rectangle rather than the desired green/gray for the entire edit
	control.
	
	This behavior can also occur with other controls such as option buttons and list
	boxes. However, an application can avoid this problem by using the SetBkMode
	function to set the background mode to TRANSPARENT. This allows the dithered
	brush pattern to show through beneath the text to achieve the desired results.
	That solution is not practical with a multiline edit control because if text is
	inserted, and the background mode has been set to TRANSPARENT, the text that is
	pushed to the right by the inserted text leaves its image behind. The result is
	text superimposed on top of other text, which quickly becomes unreadable.
	
	To partially work around this situation for a multiline edit control, use the
	GetNearestColor function to determine the nearest physical color to the desired
	color, as in the code fragment below. In this case, the entire edit control is
	gray:
	
	     case WM_CREATE:
	        {
	        HDC hDC;
	        hDC = GetDC(hWnd);
	        hGrayBrush = CreateSolidBrush(GetNearestColor(hDC,
	              RGB(64, 128, 128)));
	        ReleaseDC(hWnd, hDC);
	        hWndEdit = CreateWindow( ... ES_MULTILINE ... );
	        }
	        break;
	
	     case WM_CTLCOLOR:
	           if (HIWORD(lParam) == CTLCOLOR_EDIT)
	           // Use the following line instead of the two above for
	           // 32-bit Windows
	           // case WM_CTLCOLOREDIT:
	           {
	           // The following call creates the nearest physical
	           // color; therefore, it will be the same as the
	           // hGrayBrush created above.
	           SetBkColor(wParam, RGB(64, 128, 128));
	           SetTextColor(wParam, RGB(255, 0, 0)); // red text
	           return (DWORD)hGrayBrush;
	           }
	        else
	          return DefWindowProc(hWnd, identifier, wParam, lParam);
	        break;
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbdocfix kbdocerr kbOSWinNT350 kbOSWinNT351 kbOSWin95 kbSDKWin16 
	Technology        : kbAudDeveloper kbSDKSearch kbWin32sSearch kbWin32API kbWinSDKSearch
	Version           : WINDOWS:3.1,95; winnt:3.5,3.51
	
	=============================================================================
	

{% endraw %}
