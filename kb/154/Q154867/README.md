---
layout: page
title: "Q154867: DBWEB: How to Create a Custom Update DBX"
permalink: /kb/154/Q154867/
---

## Q154867: DBWEB: How to Create a Custom Update DBX

{% raw %}

	Article: Q154867
	Product(s): Microsoft Access Distribution Kit
	Version(s): WINDOWS:1.0,1.1
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 29-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft dbWeb, versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft dbWeb provides a default form that you can use as your Update form.
	However, with a text editor you can create a custom HTML document to use as your
	Update form. You can design the look of the form so that it resembles other HTML
	documents on your web site.
	
	MORE INFORMATION
	================
	
	The following example uses the Employees table in the sample database Nwind.mdb
	and the dbnwind data source. Before you begin the example, make sure you can
	query the Employees sample schema in the dbnwind data source of the dbWeb
	administrator.
	
	CAUTION: Following the steps in this example will modify the sample database
	Nwind.mdb and the Employees sample schema. You may want to back up the Nwind.mdb
	and Dbweb.mdb files, or use a copy of them for this example.
	
	Creating a Custom Update Form
	-----------------------------
	
	NOTE: The HTML example below uses /scripts as the cgi files folder. That is the
	default folder for Internet Information Server (IIS). If you use a different web
	server, the folder may be different. Change the path as appropriate for your web
	server. Also, if you are using dbWeb 1.0, replace dbwebc.dll with $dbwebc.exe in
	the following example.
	
	1. Using Notepad or your favorite HTML editor, type the following text into a
	  new file:
	
	        <HTML>
	        <HEAD><TITLE>Update Employee Information</TITLE></HEAD>
	        <BR>
	
	        <BODY>
	        <H2 ALIGN=CENTER>Update Employee Information</H2>
	        <BR>
	
	        <FORM ACTION="/scripts/dbweb/dbwebc.dll/Employees?update"
	        METHOD="POST">
	        <INPUT TYPE="hidden" NAME="11,Employees,Employee ID"
	        VALUE="\tobj\tEmployees\tcol\tEmployee ID\t">
	
	        <TABLE>
	        <TR><TH>Last Name:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,Last Name" VALUE="\tobj\tEmployees\tcol\tLast
	        Name\t"></TD></TR>
	        <TR><TH>First Name:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,First Name" VALUE="\tobj\tEmployees\tcol\tFirst
	        Name\t"></TD></TR>
	        <TR><TH>Title:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,Title"
	        VALUE="\tobj\tEmployees\tcol\tTitle\t"></TD></TR>
	        <TR><TH>Address:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,Address"
	        VALUE="\tobj\tEmployees\tcol\tAddress\t"></TD></TR>
	        <TR><TH>City:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,City"
	        VALUE="\tobj\tEmployees\tcol\tCity\t"></TD></TR>
	        <TR><TH>Region:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,Region"
	        VALUE="\tobj\tEmployees\tcol\tRegion\t"></TD></TR>
	        <TR><TH>Postal Code:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,Postal Code" VALUE="\tobj\tEmployees\tcol\tPostal
	        Code\t"></TD></TR>
	        <TR><TH>Country:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,Country"
	        VALUE="\tobj\tEmployees\tcol\tCountry\t"></TD></TR>
	        <TR><TH>Home Phone:</TH><TD><INPUT TYPE="text" SIZE=20 MAXLENGTH=256
	        NAME="1,Employees,Home Phone" VALUE="\tobj\tEmployees\tcol\tHome
	        Phone\t"></TD></TR>
	        <TR><TH><INPUT TYPE=submit VALUE="Submit Update"></TR></TH>
	        </TABLE>
	
	        </FORM>
	        </BODY>
	        </HTML>
	
	2. Save the file as Upempinf.htm in the dbweb subfolder of the HTML document
	  root folder (\inetsrv\wwwroot\dbweb, if IIS is your web server).
	
	Modifying the Schema
	--------------------
	
	1. Start the dbWeb Administrator.
	
	2. Double-click the dbnwind data source.
	
	3. Double-click the Employees schema.
	
	4. Click the Schema tab, and then click to select the Update check box.
	
	5. Click the QBE tab.
	
	6. In the "Data columns in selected tables" box, select Employee ID, and then
	  click Add.
	
	7. Click the Ins/Upd/Del tab.
	
	8. In the "Data columns in selected tables" box, select each of the following
	  fields, and then click Add:
	
	      Employee ID
	      Last Name
	      First Name
	      Title
	      Address
	      City
	      Region
	      Postal Code
	      Country
	      Home Phone
	
	9. In the "Update data columns" box, select Employee ID, and then click
	  Properties.
	
	10. Under Column Properties, set the Key property to Key(non updateable).
	
	11. Click the DBX tab.
	
	12. In the "Single record result output custom format file" box, click Browse to
	  find the Upempinf.htm file (in the \inetsrv\wwwroot\dbweb folder, if IIS is
	  your server).
	
	13. Click Apply.
	
	View the custom update form:
	----------------------------
	
	1. Open your favorite browser, and type the URL path to the Employees schema
	  using the getxqbe method. For dbWeb 1.1, the default path is
	  /scripts/dbweb/dbwebc.dll/Employees?getxqbe. For dbWeb version 1.0, the
	  default path is /scripts/dbweb/$dbwebc.exe/Employees?getxqbe.
	
	2. On the Employees QBE page, type 1 in the Employee ID field.
	
	3. Click the Submit Query button to run the query and invoke your custom Update
	  form.
	
	4. Change some information on the form, and then click Submit Update. You will
	  receive a success or failure message.
	
	NOTE: If Submit Query returns more than one record, you will not see the custom
	Update form you created. In this example, you must limit the query results to
	one record. However, it is possible to use this form for multiple record
	queries. Just set Upempinf.htm as the "Multi record result output custom format"
	file on the DBX tab of the Employees schema.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbAudDeveloper kbdbWebSearch kbdbWeb100 kbdbWeb110
	Version           : WINDOWS:1.0,1.1
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
