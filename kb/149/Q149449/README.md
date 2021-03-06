---
layout: page
title: "Q149449: IR Communications Driver 2.0 Relnotes.doc (Part 1 of 2)"
permalink: /kb/149/Q149449/
---

## Q149449: IR Communications Driver 2.0 Relnotes.doc (Part 1 of 2)

{% raw %}

	Article: Q149449
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): Win2000:95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This information is a copy of the information in the Relnotes.doc file included
	with the Microsoft Windows 95 Infrared Communications Driver version 2.0.
	
	MORE INFORMATION
	================
	
	Microsoft Windows 95
	Infrared Communications Driver
	Version 2.0
	Release Notes
	10 May 1996
	
	Copyright Microsoft Corporation 1996.   All Rights Reserved.
	
	Contents
	  Infrared Communications Driver, Version 2.0
	     Using the IR Communications Driver
	     Troubleshooting
	     Product Support
	
	INFRARED COMMUNICATIONS DRIVER, VERSION 2.0
	===========================================
	The Infrared Communications Driver, Version 2.0, is an optional component
	of the Windows 95 operating system. The Infrared Communications Driver
	supports hardware devices which enable networking and communications over
	the infrared media. The hardware device can be either an infrared port
	built into the platform or an infrared adapter connected to one of the
	platform's serial or parallel ports.
	
	User motivations for installing the infrared hardware device and the
	Version 2.0 Infrared communications driver are:
	
	- The user can use wireless IR links instead of serial and parallel
	  cables. For example, files can be exchanged wirelessly between two
	  computers that have an IR device and the Version 2.0 driver installed,
	  instead of using a serial or parallel cable. Files can also be printed
	  wirelessly on IR-capable printers.
	
	- The user can use wireless IR links instead of LAN cabling, if the user
	  has an IR-capable LAN access point product connected to the network
	  (see "Using the IR Communications Driver" for a list of LAN access
	  point products the Version 2.0 IR driver has been tested with).
	
	The Version 2.0 IR communications driver supports IR communications links
	running at speeds up to 115.2 kbps.
	
	USING THE IR COMMUNICATIONS DRIVER
	==================================
	This section of the Release Notes lists the hardware and software
	components on which the Version 2.0 IR communications driver has been
	tested.
	
	Notebook Computers
	------------------
	The Version 2.0 IR communications driver has been successfully tested on
	the following Windows 95 notebook computers that have built-in IR ports:
	  Gateway 2000 Liberty
	  HP Omnibook 600CT
	  HP Omnibook 4000C
	  IBM ThinkPad 701C (Butterfly)
	  Sharp PC 3050
	  TI TravelMate5000
	
	Some testing of the Version 2.0 IR driver was also done on these Windows 95
	notebooks:
	  Digital HiNote Ultra CT475
	  TI TravelMate 5000
	
	IR Adapters
	-----------
	The Version 2.0 IR driver has been successfully tested on Windows 95
	platforms with the following IR adapters connected to serial ports:
	  ACTiSYS ACT-200L Infrared Wireless Interface
	  ACTiSYS ACT-220L Infrared Wireless Interface
	  Adaptec AIRport APA-9320 External Infrared Adapter (this adapter is
	     also called the Adaptec AIRport 2000)
	  AMP PhasIR Serial Adapter
	  Extended Systems JetEye PC Infrared PC Interface (ESI-9680)
	  Parallax IR Adapter LiteLink PRA9500A
	
	To obtain any of the IR adapters listed above, contact the adapter
	manufacturer. The addresses of these manufacturers are listed in "IR
	Adapter Manufacturer Names and Addresses" at the end of this document.
	
	Applications
	------------
	The following applications have been run successfully over an IR
	communications link, using the IR communications driver and the hardware
	listed above:
	  Windows 95 Direct Cable Connection (DCC).
	  Various Windows communications applications, including HyperTerminal
	     and DynaComm.
	
	Because the IR link simulates a serial communications link, some
	communications applications may not perform as expected after they connect
	over the IR link. See "Troubleshooting" for more information. For
	instructions on running DCC over an IR link, see "Notes on Running the
	Direct Cable Connection Application Over an IR Link" later in this
	document.
	
	Printers
	--------
	Numerous Windows 95 applications have successfully printed over an IR link
	to an HP Laserjet 5P or 5MP printer, which have built-in IR ports. Numerous
	Windows 95 applications have also printed successfully over an IR link to
	other printers with an Extended Systems JetEye Infrared Printer Port ESI-
	9580 infrared adapter connected to the printer parallel port.
	
	IrLan Access Points
	-------------------
	Local area network access over an IR link has been tested with the
	following IrLan access point devices:
	  Extended Systems ESI-9910 JetEye Net Plus.
	  Hewlett-Packard NetBeam IR Infrared LAN Adapter.
	
	TROUBLESHOOTING
	===============
	Some general troubleshooting tips are:
	
	- A user must always remove any previously installed version of the IR
	  communications driver every time the driver is installed. If Version
	  1.0 of the driver is installed, it must be removed before installing
	  Version 2.0. If an early Beta release of the Version 2.0 driver is
	  installed, it must be removed before installing the current Version 2.0
	  release. Instructions for removing the IR communications driver are in
	  "An Optional Step: Removing the IR Communications Driver."
	
	- If the user changes the IR adapter model that is connected to the
	  computer, the user must remove the installed IR communications driver
	  and reinstall it, specifying the new IR adapter type. Instructions for
	  removing the IR communications driver are in "An Optional Step:
	  Removing the IR Communications Driver."
	
	- During installation of the IR communications driver, a user may select
	  the wrong port when the Add Infrared Device Wizard prompts for the
	  physical COM port to which the IR device is connected. If the user
	  selects the wrong COM port, the IR device will be unable to discover
	  another IR device within range. Reasons why the user may select the
	  wrong COM port vary, ranging from reasoning such as "there is only one
	  physical COM port for the IR adapter to be connected to so it must be
	  COM1" to mislabeled COM ports on the computer case to the simple fact
	  that the user doesn't know which COM port to select and doesn't know how
	  to find out. A troubleshooting procedure is:
	     1. Put an actively searching IR device close to the computer's IR
	        device.
	     2. Click the Infrared Monitor Options tab and then choose a
	        different communications port (for
	          example, COM1 instead of COM2).
	     3. Continue selecting different COM ports in this way until the IR
	        device on the computer discovers the nearby IR device.
	  Note that the alternatives displayed in the IrMon Options tab are
	  always based on the internal wiring of the computer platform:
	   - COM1 always means a COM port wired to IRQ 4 and I/O address range
	     0x3F8 to 0x3FF.
	   - COM2 always means wired to IRQ 3 and 0x2F8 to 0x2FF.
	   - Physical COM3 always means IRQ 4 and 0x3E8 and 0x3EF.
	   - Physical COM4 always means IRQ5 and 0x2E8 and 0x2EF.
	
	- To get two IR devices to discover each other, the user may have to
	  realign the IR devices so they point right at each other, move them
	  closer together, and/or change the batteries in an IR adapter or plug
	  the AC power into an IR adapter. The devices must be three feet apart,
	  or less, and the angle of the cone of IR transmission is 30 degrees.
	  Some devices work best if kept at least six inches apart.
	
	- If an IR adapter is attached to a COM port that is using an 8250 UART
	  instead of a 16550 UART, or if an IR adapter is connected to a
	  relatively slow computer (such as a 386 running at 20 MHz), the user
	  might need to use the Limit Connection Speed To option in the Infrared
	  Monitor Options tab to limit the connection speed to 19.2 kbps. After
	  establishing a successful IR connection at this speed, the user can use
	  the Limit Connection Speed To option to experiment with establishing a
	  connection at a higher speed on their particular computer.
	
	- If the IR Monitor Options tab is used to change the port the IR adapter
	  is attached to while IR communications are in progress, the IR
	  connection is lost without prompting the user to verify that it is OK
	  to disconnect.
	
	- Communication over a virtual COM port link between two computers may
	  not be reliable if a printer's IR adapter is also within range. The
	  user should move the printer's IR adapter out of range.
	
	- A user should not suspend a Windows 95 computer while an IR connection
	  is established. Wait until the IR link is disconnected or force a
	  disconnection before putting the computer in suspend mode. For example,
	  if an IrLan connection is established on a laptop, the user must always
	  move the laptop out of range of the IrLan access point before
	  suspending the system or closing the laptop lid. Otherwise, the
	  connection remains active and over time can drain the battery.
	
	- Connecting and disconnecting over a low-speed IR link or over a poor-
	  quality link can take a long period of time (a few seconds), during
	  which time the screen will appear to be frozen. To work around this,
	  the user should use a higher-speed connection and/or take steps to
	  improve the quality of the connection by, for example, realigning the
	  IR devices so they point right at each other, moving the devices closer
	  together, changing the batteries in an IR adapter, or plugging the AC
	  power into an IR adapter.
	
	Troubleshooting Tips Specific to Using IrLan Access Point Devices Are
	---------------------------------------------------------------------
	- Do not assume that because an IR device on a PC communicates with an IR
	  device on another PC at 115.2 kbps that the IR device will also
	  communicate with an IrLan access point device at that speed.  For
	  example, suppose a user has two PC-based IR devices that have
	  negotiated a link speed of 115.2 kbps. Then if the user points one of
	  the devices at an IrLan access point device, these two devices can
	  negotiate a link speed of 115.2 kbps but no subsequent communication
	  takes place (the PC has no access to the network through the IR link).
	  No error message is displayed in this case.
	- Extended Systems ESI-9910 JetEye Net Plus users utilizing NETBEUI may
	  receive an error message when copying large files (for example, 5 MB
	  files) to a network drive. If this happens, call Extended Systems, Inc.
	  product support for NETBEUI configuration changes. For Extended
	  Systems, Inc. contact information, see the topic "IR Adapter
	  Manufacturer Names and Addresses."
	- If there is a problem establishing an IR link to an IrLan access point
	  device when the network is also connected to a network interface card
	  in the computer, try disconnecting the LAN from the network interface
	  card. Restart the computer and make sure the computer IR device and the
	  LAN access point IR port are within range. Then use the Infrared icon
	  in the Control Panel to activate the IR link between the computer and
	  the LAN access point device.
	- The IPX protocol may not communicate over an IrLan access point. This
	  can be caused by the Dial-Up Adapter becoming the primary IPX adapter
	  and no other adapter, such as the IrLan adapter, can take over. To get
	  around this problem, the user can create a profile that does not
	  contain the dial-up adapter and use it when accessing the net through
	  IrLan.
	- During a file copy to a NetWare server running burst mode, if the IR
	  connection between the computer and the IrLan access point is
	  disconnected (for example, the IR beam is blocked), the file transfer
	  cannot recover and the computer screen will stay the same indefinitely.
	  If this happens often, turn off burst mode to enable recovery from a
	  disconnection. There will be performance degradation with burst mode
	  off.
	- Using the virtual parallel port connection to an Extended Systems ESI-
	  9910 JetEye Net Plus IrLan access point to send data to a printer may
	  result in a program fault. To get around this, use the virtual serial
	  port on the IrLan access point to reach the printer.
	
	Troubleshooting Tips Related to Using
	Particular Applications Over IR Links Are
	-----------------------------------------
	- If the Windows 95 application HyperTerminal is used to transfer files,
	  there may be trouble doing file transfers successfully over an IR link.
	  If the Zmodem protocol fails with a link speed of 115.2 kbps, use the
	  IR Monitor Limit Connection Speed To tab to limit the link speed to
	  19.2 kbps and then retry the Zmodem file transfer.
	- When the Windows 95 application Direct Cable Connection (DCC) is run to
	  establish the connection between the host and guest computers, the
	  guest computer may display the message "Direct Cable Connection was
	  unable to display shared folders of the host computer" and prompt the
	  user to enter the computer name of the host computer. A convenient way
	  to find the computer name of the host computer is on the Status tab of
	  the Infrared Monitor interface screen.
	- When the Windows 95 application Direct Cable Connection (DCC) is run to
	  establish an IR connection between the host and guest computers, DCC
	  prompts the user to select a communications port (this procedure is
	  described in the topic "Establishing and Using the DCC IR Link Between
	  Host and Guest"). Selecting the virtual Infrared port in this step will
	  fail (DCC announces the virtual port is not available) in the rare case
	  that the user has suspended the Windows 95 operating system before
	  invoking DCC in a session. Restart Windows 95 to begin a new session
	  and DCC will work over an IR link.
	
	A Troubleshooting Tip Related to Developing an IrDA
	Standard IrCOMM Component for an IR Communications Driver Is
	------------------------------------------------------------
	- The IrCOMM implementation in the IR communications driver that runs on
	  Windows 95 supports full emulation of 9-wire connections, but does not
	  support emulation of 3-wire cooked connections. A specific example of
	  this is the inability to print over an IR virtual COM port from the MS-
	  DOS prompt, which uses a 3-wire cooked connection. IrDA drivers
	  developed for platforms designed to communicate with Windows 95
	  platforms over IR links must implement full emulation of 9-wire
	  connections (as specified in the IrDA IrCOMM specification). For
	  example, a pair of handheld computer platforms may communicate with
	  each other over IR links using 3-wire cooked emulation. However, if the
	  user also expects to use one of the handhelds to communicate with a
	  Windows 95 computer then the handheld IR driver must implement 9-wire
	  connections.
	
	Troubleshooting Tips Related to Specific Infrared Hardware Are
	--------------------------------------------------------------
	- The Adaptec AIRport 2000 infrared adapter can be powered by either the
	  serial port, installed AA batteries, or an external power supply. In
	  some cases, the serial port may not provide sufficient power for the
	  operation of the adapter. This can cause reduced operating range and/or
	  a failure to find another IR device which is nearby and aligned
	  correctly. If such a problem is suspected, connect an AC adapter or add
	  four AA batteries to the battery compartment in the infrared adapter.
	  This will assure sufficient power. In some instances, the user may need
	  to separate the adapter by at least six inches from the other IR device.
	- If an ActiSys 220L IR adapter is attached to a computer and used to
	  print to a printer that is using an Extended Systems ESI-9580 printer
	  IR adapter, or for printing to an HP DeskJet 340, the Options tab in
	  the Infrared Monitor must be used to limit the connection speed to 19.2
	  kbps to print successfully. If the IR devices are allowed to
	  automatically negotiate the connection speed without setting this
	  limit, they will negotiate a higher connection speed and an application
	  will not be able to print.
	- The TI TravelMate 5000 may communicate over an IR link only at very low
	  speeds (9600 bps).
	- The Sharp PC 3050 may communicate over an IR link only at speeds
	  between 9600 bps and 19.2 kbps.
	- For the HP Omnibook 4000C or an HP Omnibook 600CT, which have built-in
	  infrared ports, a special echo-canceling serial driver must be
	  installed in addition to the components that make up the IR
	  communications driver. The echo-canceling driver, along with
	  instructions on how to install it, are available from Hewlett-Packard.
	
	For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Additional query words: irda irda2 ir w95ir.exe
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : Win2000:95
	
	=============================================================================
	

{% endraw %}
