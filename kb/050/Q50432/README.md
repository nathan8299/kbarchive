---
layout: page
title: "Q50432: Mac Hyp: Write-Protected Stacks in HyperCard"
permalink: /kb/050/Q50432/
---

## Q50432: Mac Hyp: Write-Protected Stacks in HyperCard

{% raw %}

	Article: Q50432
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:2.0,2.0a,2.0b,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, versions 2.0, 2.0a, 2.0b, 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The information in this article about write-protected stacks in Microsoft Mail
	is taken from the "HyperCard Version 1.2 Update" leaflet.
	
	MORE INFORMATION
	================
	
	HyperCard stacks can be write-protected. You can look at a write-protected stack
	and make copies of all or part of it, but you can't change it.
	
	You can recognize a write-protected stack because a padlock appears to the right
	of the rightmost menu title on the menu bar. When a stack is write-protected,
	you can't type into any fields, and you can't use certain menu items:
	
	- Compact Stack
	
	- Delete Stack
	
	Stacks are write-protected in a number of ways:
	
	- The stack is on a CD-ROM.
	
	- The stack is on a file server in a folder whose access privileges are set to
	  Read Only.
	
	- The Locked box is checked in the stack's Get Info box in the Finder.
	
	- The stack is on a locked 3.5-inch disk.
	
	- Can't Modify Stack is checked in the stack's Protect Stack dialog box.
	
	When the stack is on a write-protected medium (for example, a locked disk, a
	CD-ROM, a locked folder on a file server), HyperCard automatically puts a check
	mark into the Can't Modify Stack option; you can't undo it.
	
	To make permanent changes to such a stack, you'll first have to remove the
	write-protection. In many cases, copying a stack to an unlocked disk makes the
	stack modifiable. However, if a user has checked Can't Modify Stack in the
	stack's Protect Stack dialog box, or if the Locked box is checked in the stack's
	Get Info box in the Finder, you'll have to uncheck the proper boxes after
	copying before you can make stack changes.
	
	Additional query words: 2.00 2.00a 2.00b 3.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN300 kbMailATN200 kbMailATN200a kbMailATN200b
	Version           : WINDOWS:2.0,2.0a,2.0b,3.0
	
	=============================================================================
	

{% endraw %}
