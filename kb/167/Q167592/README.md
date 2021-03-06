---
layout: page
title: "Q167592: ACC97: SourceSafe Integration Tips"
permalink: /kb/167/Q167592/
---

## Q167592: ACC97: SourceSafe Integration Tips

{% raw %}

	Article: Q167592
	Product(s): Microsoft SourceSafe
	Version(s): 4.0 4.0a 5.0 97
	Operating System(s): 
	Keyword(s): kbinterop
	Last Modified: 01-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 4.0a, 5.0 
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	Moderate: Requires basic macro, coding, and interoperability skills.
	
	SUMMARY
	=======
	
	This article contains tips to help you use the Source Code Control component of
	Microsoft Office 97 Developer Edition (ODE) Tools with Microsoft Visual
	SourceSafe.
	
	The article is divided into three sections: Environment, Security, and Usage.
	
	MORE INFORMATION
	================
	
	Environment
	-----------
	
	- If you move, copy, or rename a database that is under source code control,
	  you will no longer be able to use the source code control features with that
	  database. However, you can recreate the database from the source code control
	  project, and re-enable source code control features by pointing to SourceSafe
	  on the Tools menu, and then clicking Create Database From SourceSafe Project.
	
	- The Microsoft Access Source Code Control component is specifically designed
	  to manage Microsoft Access objects. It is possible to use Microsoft Visual
	  SourceSafe or another source code control program to include non-Access files
	  in the same source code control project that contains your database objects.
	  However, even though those files appear as part of your project when you view
	  them in Microsoft Visual SourceSafe, you cannot check any files in or out, or
	  get the latest version of the files. Manage your non-Access files in a
	  separate source code control project.
	
	- If you use a localized version of Microsoft Office 97 Developer Edition
	  Tools, the user interface for the Microsoft Access Source Code Control
	  component appears in the language for that version. If that is not the case,
	  check the Regional Settings option in Control Panel to be sure it contains
	  the correct language settings for the localized version of Microsoft Office
	  97 Developer Edition Tools you are using.
	
	Security
	--------
	
	- When you add a database to source code control, any security features that
	  you have implemented are removed from the database before the objects are
	  added to the source code control project. However, by default Microsoft
	  Visual SourceSafe maintains its own security on projects so that each user
	  either has read-write access (the ability to edit files) or read-only access.
	  You can set those permissions for an entire project or for specific users.
	  After you finish developing your application and remove it from source code
	  control, you can re-implement Microsoft Access security features before you
	  distribute the application.
	
	  For more information about issues using Microsoft Visual SourceSafe and a
	  secured Microsoft Access database, please see the following article in the
	  Microsoft Knowledge Base:
	
	  Q162933 ACC97: User Without Permissions Can Check Out an Object in VSS
	
	
	- If a developer checks out an object, and then forgets his/her password,
	  leaves the company, or is out of the office, the Microsoft Visual SourceSafe
	  administrator can start the Visual SourceSafe Administrator program and
	  change or delete that user's password. Then you can log on to the project
	  with the new password and check in the objects or undo the check out.
	
	Usage
	-----
	
	- Always check out an object that is under source code control before you make
	  changes to the design of the object.
	
	- If you create a query using a query wizard, you are not prompted to add the
	  query to source code control when you save it. To add the query to source
	  code control, point to SourceSafe on the Tools menu, and then click Add
	  Objects To SourceSafe.
	
	- If you use the Linked Table Manager to refresh the link to a table that is
	  under source code control, and you do not have Data and Misc. Objects checked
	  out, Microsoft Access does not prompt you to check it out. When you do check
	  out Data and Misc. Objects, if the data to which the table was originally
	  linked is not available, you receive two error messages and then the linked
	  tables are deleted.
	
	  For more information about this topic, please see the following article in the
	  Microsoft Knowledge Base:
	
	  Q163346 ACC97: Linked Table Manager Doesn't Prompt You to Check Out Data
	
	
	- If you modify a custom toolbar without checking out Data and Misc. Objects,
	  your changes will be lost when you synchronize the source code control
	  project with your database. Check out the Data and Misc. Objects object
	  before you make changes to your custom toolbars.
	
	  For more information about this topic, please see the following article in the
	  Microsoft Knowledge Base:
	
	  Q162825 ACC97: Customizing Command Bar Does Not Prompt for Check-Out
	
	- Each source code control project must contain only one Data and Misc. Objects
	  (.acb) file. If you add a second Data and Misc. Objects file to a source code
	  control project, you receive an error when you use the Share Objects, Create
	  Database From SourceSafe Project, or Refresh Object Status commands.
	
	- Before you create a table using a macro, a make-table query, or Visual Basic
	  code, first check out Data and Misc. Objects. If you do not, the table
	  appears to be created, and even appears to be under source code control, but
	  if you close the database and recreate it from the source code control
	  project, or if you use the Get Latest Version command to retrieve the most
	  recent version of Data and Misc. Objects, the table is removed because it was
	  never actually added to source code control.
	
	  For more information about this and related topics, please see the following
	  articles in the Microsoft Knowledge Base:
	
	  Q163348 ACC97: Tables That Appear to Be Checked In in VSS Are Not
	
	  Q159690 ACC97: Problem Adding Objects Created in VBA to SourceSafe
	
	
	- If you open an object in Design view using Visual Basic code, you are not
	  prompted to check out the object. Any changes you make will be lost when you
	  synchronize the source code control project with your database. If you plan
	  to change the design of an object with Visual Basic code, check out the
	  object first.
	
	- When your team finishes development work on a Microsoft Access application,
	  you must remove the database from source code control so you can distribute
	  it or replicate it. To remove a Microsoft Access database from source code
	  control, make sure all changes to the database are checked in. Then point to
	  Database Utilities on the Tools menu, and click Compact Database. When
	  prompted if you want to remove the compacted database from source code
	  control, click Yes. All source code control properties are removed from the
	  database.
	
	  NOTE: You should not attempt to replicate a database while it is under source
	  code control.
	
	- You can work on a database even when you aren't connected to the source code
	  control provider. However, before you disconnect from the server, check out
	  any objects that you plan to modify.
	
	- When a database is under source code control, only one user at a time can
	  connect to it or open it. Create a copy of the database from the project for
	  each developer who will work on it. To do so, on each developer's computer,
	  point to SourceSafe on the Tools menu, and then click Create Database From
	  SourceSafe Project.
	
	Additional query words: SCC ACCSCC VSS source safe
	
	======================================================================
	Keywords          : kbinterop 
	Technology        : kbSSafeSearch kbOfficeSearch kbAudDeveloper kbOffice97Search kbOffice97 kbSSafe400 kbSSafe400a kbSSafe500 kbOffice97DevSearch
	Version           : 4.0 4.0a 5.0 97
	Hardware          : x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
