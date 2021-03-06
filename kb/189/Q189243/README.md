---
layout: page
title: "Q189243: No Error Displays When Admin Is Running During Move Server"
permalink: /kb/189/Q189243/
---

## Q189243: No Error Displays When Admin Is Running During Move Server

{% raw %}

	Article: Q189243
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you use the Move Server utility to change the Enterprise name of an
	Exchange Server computer while the Exchange Server Administrator program is
	running, a system crash will occur and produce the following call stack:
	
	   CBaseNode::RemoveChild(CBaseNode * const 0x00a53a70, CBaseNode *
	   0x004cef1e) line 2262 + 6 bytes
	   CBaseHList::DeleteItem(CBaseHList * const 0x00a53a70, CBaseNode *
	   0x004d1c9c) line 1382
	   CHmtNode::ScRefreshNode(CHmtNode * const 0x00a53a70) line 4362 + 12 bytes
	   CHList::ScRefreshList(CHList * const 0x00a53a70) line 1964
	   CServerListForm::OnReloadEnterprise(CServerListForm * const 0x00a53a70, int
	   4383655) line 9972
	   CServerListForm::OnRefresh(CServerListForm * const 0x00a53a70) line 4131
	   CBaseForm::FProcessMenu(CBaseForm * const 0x00a53a70, unsigned int 4371442)
	   line 2325
	   CServerListForm::FProcessMenu(CServerListForm * const 0x00a53a70, unsigned
	   int 5329784) line 1198 + 8 bytes
	   CBaseFrame::LWndProc(CBaseFrame * const 0x00a53a70, unsigned int 4302121,
	   unsigned int 273, long 65544) line 3509 + 15 bytes
	   CAdminFrame::LWndProc(CAdminFrame * const 0x00a53a70, unsigned int 5330311,
	   unsigned int 273, long 67512) line 391
	   CBaseFrame::LWndProcStatic(HWND__ * 0x77e71ab7, unsigned int 1638898,
	   unsigned int 273, long 67512) line 3690
	   USER32! 77e71ab7()
	
	No errors or messages are displayed when you start the Move Server utility to
	alert you that the Exchange Server Administrator program is running and should
	be stopped before you begin.
	
	WORKAROUND
	==========
	
	Stop the Exchange Server Administrator program before starting the Move Server
	utility.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server 5.5.
	We are researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	Additional query words: pilgrim post-SP1
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WINDOWS:5.5
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
