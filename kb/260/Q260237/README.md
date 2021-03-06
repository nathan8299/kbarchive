---
layout: page
title: "Q260237: Visual FoxPro 6.0 Sample: Using a PictureClip Control"
permalink: /kb/260/Q260237/
---

## Q260237: Visual FoxPro 6.0 Sample: Using a PictureClip Control

{% raw %}

	Article: Q260237
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbfile kbsample kbActiveX kbCtrl kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport
	Last Modified: 11-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	PicClip.exe is a sample that demonstrates how to use an ActiveX PictureClip
	control to select an area from a source bitmap and display the image in an
	ActiveX FoxHWND control (FoxHWND.ocx). By using the PictureClip control
	(PicClp32.ocx), the user can select a specific area from a source bitmap as an
	object that can then be passed to another control that is capable of accepting
	an object reference.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  PicClip.exe
	  (http://download.microsoft.com/download/vfox60/sample3/6/win98/en-us/PicClip.exe)
	
	Release Date: May-24-2000
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	The PictureClip control provides an efficient mechanism for storing multiple
	picture resources in a single bitmap file. Instead of using multiple bitmaps or
	icons, you need to create a source bitmap that contains all of the bitmap images
	that are required by your application. When you need to display an individual
	bitmap, use the PictureClip control to select the region in the source bitmap
	that contains the portion of the bitmap that you need.
	
	You can specify the clipping region in the source bitmap in one of two ways:
	
	- Select any portion of the source bitmap as the clipping region. Specify the
	  upper-left corner of the clipping region by using the ClipX and ClipY
	  properties. Specify the area of the clipping region by using the ClipHeight
	  and ClipWidth properties. This method is useful when you want to view a
	  random portion of a bitmap.
	
	- Divide the source bitmap into a specified number of rows and columns. The
	  result is a uniform matrix of picture cells numbered 0, 1, 2, and so on. You
	  can then display individual cells by using the GraphicCell property. This
	  method is useful when the source bitmap contains a palette of icons that you
	  want to display individually, such as in a toolbar bitmap.
	
	Because the PictureClip control returns an object rather than a Bitmap, an image
	control cannot be used to display the selected area of the source bitmap. To
	display the selected area of the source bitmap, use a FoxHWND control to accept
	and display the object.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by John Desch,
	Microsoft Corporation.
	
	
	Additional query words: PicClip
	
	======================================================================
	Keywords          : kbfile kbsample kbActiveX kbCtrl kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	
	=============================================================================
	

{% endraw %}
