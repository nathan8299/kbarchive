---
layout: page
title: "Q181289: HOWTO: Pass Structures to a DLL"
permalink: /kb/181/Q181289/
---

## Q181289: HOWTO: Pass Structures to a DLL

{% raw %}

	Article: Q181289
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbcode kbnokeyword kbvfp300 kbvfp500 kbvfp600
	Last Modified: 06-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Many DLLs require that the calling program pass a structure. FoxPro can pass by
	reference a string of the same length as the required structure. Depending on
	the datatype, some variables need to be converted to the proper format. For
	instance, DWORD is a low-high format, so any 4-byte values need to be converted
	to a string in the DWORD format. DLLs may also return values that need to be
	converted from a string in a low-high format to an integer value.
	
	MORE INFORMATION
	================
	
	The Win32 API function GetSystemInfo requires that a pointer to a structure be
	passed to the function. The following example demonstrates how to make the call
	then convert the elements of the returned string using the StrToLong function.
	The LongToStr function to do the reverse is also included.
	
	Copy this code into a program file (.prg) and run the program. This program uses
	GetSystemInfo to return information about a computer's processor and memory.
	
	The code is listed below:
	
	     #DEFINE CR CHR(13)
	     #DEFINE PROCESSOR_INTEL_386 386
	     #DEFINE PROCESSOR_INTEL_486 486
	     #DEFINE PROCESSOR_INTEL_PENTIUM 586
	     #DEFINE PROCESSOR_MIPS_R4000 4000
	     #DEFINE PROCESSOR_ALPHA_21064 21064
	
	     DECLARE GetSystemInfo IN win32api STRING @SystemInfo
	     DECLARE GlobalMemoryStatus IN win32api STRING @MemStat
	     SystemInfo = SPACE(36)
	     m.stru = LongToStr(32) + REPLICATE(CHR(0), 28)
	     =GetSystemInfo(@SystemInfo)
	     =GlobalMemoryStatus(@m.stru)
	     m.oem_id = StrToLong(LEFT(SystemInfo, 4))
	     m.page_size = StrToLong(SUBSTR(SystemInfo, 5, 4))
	     m.minappaddr = StrToLong(SUBSTR(SystemInfo, 9, 4))
	     m.maxappaddr = StrToLong(SUBSTR(SystemInfo, 13, 4))
	     m.processormask = StrToLong(SUBSTR(SystemInfo, 17, 4))
	     m.num_processors = StrToLong(SUBSTR(SystemInfo, 21, 4))
	     m.processortype = StrToLong(SUBSTR(SystemInfo, 25, 4))
	     m.processorname = ""
	     m.memoryload = StrToLong(SUBSTR(m.stru, 5, 4))
	     m.totalphys = StrToLong(SUBSTR(m.stru, 9, 4))
	     m.availphys = StrToLong(SUBSTR(m.stru, 13, 4))
	     m.totalpagefile = StrToLong(SUBSTR(m.stru, 17, 4))
	     m.availpagefile = StrToLong(SUBSTR(m.stru, 21, 4))
	     m.totalvirtual = StrToLong(SUBSTR(m.stru, 25, 4))
	     m.availvirtual = StrToLong(SUBSTR(m.stru, 29, 4))
	     DO CASE
	     CASE m.processortype = PROCESSOR_INTEL_386
	        m.processorname = "INTEL 386"
	     CASE m.processortype = PROCESSOR_INTEL_486
	        m.processorname = "INTEL 486"
	     CASE m.processortype = PROCESSOR_INTEL_PENTIUM
	        m.processorname = "INTEL Pentium"
	     CASE m.processortype = PROCESSOR_MIPS_R4000
	        m.processorname = "MIPS R4000"
	     CASE m.processortype = PROCESSOR_ALPHA_21064
	        m.processorname = "ALPHA 21064"
	     ENDCASE
	     m.allocationgranularity = StrToLong(SUBSTR(SystemInfo, 29, 4))
	     m.reserved = StrToLong(SUBSTR(SystemInfo, 33, 4))
	     =MESSAGEBOX("OEM ID:" + STR(m.oem_id) + CR + ;
	      "Page Size: " + STR(m.page_size) + CR + ;
	      "Minimum application address: " + STR(m.minappaddr) + CR +;
	      "Maximum application address: " + STR(m.maxappaddr) + CR + ;
	      "Processor mask: " + STR(m.processormask) + CR + ;
	      "Number of processors: " + STR(m.num_processors) + CR + ;
	      "Allocation granularity: " + STR(m.allocationgranularity) + CR + ;
	      "Percent memory in use: " + STR(m.memoryload) + CR + ;
	      "Bytes of physical memory present: " + STR(m.totalphys) + CR + ;
	      "Bytes available physical memory: " + STR(m.availphys) + CR + ;
	      "Bytes of paging file: " + STR(m.totalpagefile) + CR + ;
	      "Bytes available paging file: " + STR(m.availpagefile) + CR + ;
	      "Total virtual memory: " + STR(m.totalvirtual) + CR + ;
	      "Available bytes virtual memory: " + STR(m.availvirtual),0+64+0)
	
	     *-- The following function converts a long integer to an ASCII
	     *-- character representation of the passed value in low-high format.
	     ******************
	     FUNCTION LongToStr
	     ******************
	     * Passed : 32-bit non-negative numeric value (lnLongval)
	     * Returns : ascii character representation of passed value in low-high
	     * format (lcRetstr)
	     * Example :
	     *   m.long = "999999"
	     *   m.longstr = long2str(m.long)
	
	     PARAMETERS lnLongval
	
	     PRIVATE i, lcRetstr
	
	     lcRetstr = ""
	     FOR i = 24 TO 0 STEP -8
	        lcRetstr = CHR(INT(lnLongval/(2^i))) + lcRetstr
	        lnLongval = MOD(lnLongval, (2^i))
	     NEXT
	     RETURN lcRetstr
	
	     *-- The following function converts a string in low-high format to a
	     *-- long integer.
	     ******************
	     FUNCTION StrToLong
	     ******************
	     * Passed:  4-byte character string (lcLongstr) in low-high ASCII format
	     * Returns:  long integer value
	     * Example:
	     * m.longstr = "1111"
	     * m.longval = str2long(m.longstr)
	
	     PARAMETERS lcLongstr
	
	     PRIVATE i, lnRetval
	
	     lnRetval = 0
	     FOR i = 0 TO 24 STEP 8
	        lnRetval = lnRetval + (ASC(lcLongstr) * (2^i))
	        lcLongstr = RIGHT(lcLongstr, LEN(lcLongstr) - 1)
	     NEXT
	
	     RETURN lnRetval
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbnokeyword kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
