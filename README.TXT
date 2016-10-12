README.TXT

NOTES ON MS-DOS 6.21
====================
This version of MS-DOS does not support data compression. It differs 
from MS-DOS 6.2 as follows:

 * DoubleSpace is not included.
 * ScanDisk will not run on compressed drives.
 * The Backup programs do not compress data while backing up.
 * You cannot use the Backup programs to restore backups made with 
   MS-DOS 6 or 6.2 Backup (unless you disabled the Compress Backup 
   Data option before backing up). To restore backups made with MS-DOS 6 
   or 6.2, use the backup programs that came with those versions of MS-DOS.

Note: Because the MS-DOS 6 USER'S GUIDE is in the process of revision,
      the manual you receive might describe features that are not 
      available in this version of MS-DOS.

This file provides important information not included in the
MICROSOFT MS-DOS 6 USER'S GUIDE or in MS-DOS Help.

This file is divided into the following major sections:

1. Setup
2. MemMaker, EMM386, and Memory Management
3. Windows
4. Hardware Compatibility with MS-DOS 6.21
5. Microsoft Programs
6. Third-Party Programs

If the subject you need information about doesn't appear in
this file, you might find it in one of the following text
files included with MS-DOS:

* NETWORKS.TXT, which describes how to update your network software
  for use with MS-DOS 6.21.

For information about features new to MS-DOS 6.21, type HELP WHATSNEW
at the command prompt.

This file contains the following topics:

1. Notes on Setup
   1.1  You deleted files from the directory that Setup needs
	  to install the optional programs.
   1.2  You need to install MS-DOS manually.
   1.3  Additional Keyboard and Codepage Support
   1.4  Switching Between Modes on Dual-Mode Keyboards
2. MemMaker, EMM386, and Memory Management
   2.1  Intel Expanded-Memory Driver (EMM.SYS)
   2.2  Running MemMaker on a Computer with PC-NFS
   2.3  You have a Super VGA display and want to conserve memory.
   2.4  Using MemMaker with IBM LAN
   2.5  MemMaker and Adaptec SCSI devices
   2.6  Running MemMaker on a computer with PC Tools RAMBoost
   2.7  EMM386 detects an error in an application
   2.8  MemMaker no longer aggressively scans upper memory by default
   2.9  Additional MemMaker Troubleshooting Information
3. Windows
   3.1  Your computer uses a Windows 3.0 permanent swap file.
4. Hardware Compatibility with MS-DOS 6.21
   4.1  Hardcard
5. Microsoft Programs
   5.1  Microsoft Anti-Virus
   5.2  Running Microsoft Backup for MS-DOS under Windows
   5.3  Backup for Windows stops running at the end of the 
	  compatibility test
   5.4  Running Microsoft Backup with TI4000 and Gateway NOMAD computers
   5.5  Microsoft Defragmenter
6. Third-party Programs
   6.1  4DOS and NDOS
   6.2  Above Board 286 and Above Board Plus Installation
	  Programs
   6.3  CodeView
   6.4  Colorado Tape Backup
   6.5  Fastback Plus
   6.6  Norton Desktop for Windows 2.0
   6.7  PC Tools

1. NOTES ON SETUP
================

1.1 You deleted files from the directory that Setup needs
    to install the optional programs.
---------------------------------------------------------
If you typed SETUP /E at the command prompt, Setup displayed
the "Setup did not find the files it needs in the directory
specified" message, and you think you deleted the files from
your hard disk, carry out the following procedure.

1. Reinstall MS-DOS 6.21.

   Follow the instructions on your screen. When Setup displays
   the "This version of MS-DOS 6.21 is designed for computers that
   do not yet have an operating system" message, choose to
   continue Setup.

2. After Setup is finished, insert Setup Disk 1 in drive A,
   and type A:SETUP /E at the command prompt.

1.2 You need to install MS-DOS manually.
----------------------------------------
If you need to install MS-DOS manually, carry out the following procedure:

1. Insert Setup Disk 1 in drive, and restart your computer.

2. After the first screen appears, quit Setup by pressing F3 twice.

3. Transfer your system files to your hard disk by typing SYS A: C:
   at the command prompt.

4. Create a directory on your hard disk that will contain your MS-DOS 6.21
   files.

5. Copy all the decompressed files (files without an underscore in
   their extension) on Setup Disk 1 to your MS-DOS directory.

6. Use the EXPAND command to decompress the rest of the files on your Setup
   disks and copy them to your MS-DOS directory. You must expand the
   compressed files one at a time, and specify a new extension for each
   one. For example, to decompress the EGA.SY_  file and copy it to the 
   DOS directory, type the following at the command prompt:

   A:EXPAND EGA.SYS C:\DOS\EGA.SYS
   
   For more information about the EXPAND command and the location and
   extensions of specific files, see the PACKING.LST file on the Setup
   disks.
   
7. Create an AUTOEXEC.BAT and CONFIG.SYS file, and store them in the root 
   directory of drive C. For more information about creating these files, 
   see the chapter "Configuring Your System" in the MICROSOFT MS-DOS 6
   USER'S GUIDE.

8. Restart your computer.

1.3   Additional Keyboard and Codepage Support
----------------------------------------------
MS-DOS 6.21 includes the KEYBRD2.SYS and EGA2.CPI files, which
offer additional keyboards and codepages. You use these files just
as you would the KEYBOARD.SYS and EGA.CPI files. MS-DOS also
includes new country settings in COUNTRY.SYS.

The KEYBRD2.SYS file is essentially similar to KEYBOARD.SYS. 
The differences between KEYBOARD.SYS and KEYBRD2.SYS are:

 o  KEYBRD2.SYS contains support for the following keyboards, which
    are not supported by KEYBOARD.SYS:

    Country/Language             Keyboard layout   Keyboard ID
    ----------------             ---------------   -----------
    Canada (standard CAN/CSA-Z keyboard)   cf      243.200-92
    Brazil (secondary standard keyboard)   br      274, 275
    Greece                                 gk      319
    Iceland                                is      161
    Romania                                ro      333
    Turkish                                tr      440, 179

 o  The KEYBRD2.SYS file does not include support for the following
    keyboards supported by KEYBOARD.SYS:

       Switzerland (German)
       Switzerland (French)
       Japan               

 o  The KEYBRD2.SYS file provides access to a few keyboards by keyboard
    layout (two-letter code) only. KEYBOARD.SYS provides access to these 
    keyboards by either keyboard layout or keyboard ID. The affected 
    keyboards are:

       Poland
       Czechoslovakia (Czech)
       Czechoslovakia (Slovak)
       Yugoslavia
       Hungary

 o  KEYBRD2.SYS contains changes to the German keyboard that are
    not in KEYBOARD.SYS. In the German keyboard, the SHIFT lock 
    behavior of the top row of the keyboard now remains unaffected, 
    and is now functionally the same as the US keyboard (that is,
    "typewriter mode" has been removed).

The EGA2.CPI file is similar to the EGA.CPI file, except that the two
files contain different code pages. EGA2.CPI contains the following:

    850 - Multilingual (in both EGA2.CPI and EGA.CPI)
    852 - Eastern European (in both EGA2.CPI and EGA.CPI)
    857 - Turkish
    861 - Icelandic
    869, 737 - Greek

MS-DOS 6.21 includes new country settings in COUNTRY.SYS that use the
new keyboards and code pages.  COUNTRY.SYS contains the following
countries with their supported code pages:
    
    Country or language    Country       Character sets
			   code
    ------------------------------------------------------
    Greece                 030           869, 737
    Iceland                354           861, 850
    Romania                040           852, 850
    Turkish                090           857, 850
					   
You use the KEYBRD2.SYS and EGA2.CPI files just as you would 
KEYBOARD.SYS and EGA.CPI. These files can be used in any combination.

For example, to use the new Icelandic settings, carry out the following
steps:

1. Add the following commands to your AUTOEXEC.BAT file:

   REM ICELAND SETTINGS
   MODE CON CP PREPARE=((861) C:\DOS\EGA2.CPI)
   MODE CON CP SELECT=861
   KEYB IS,,C:\DOS\KEYBRD2.SYS

2. If you also need support for codepage 850 (Multilingual), add 
   the following commands to your CONFIG.SYS file:
		 
   REM ICELAND SETTINGS
   COUNTRY=354,861,C:\DOS\COUNTRY.SYS
   DEVICE=C:\DOS\DISPLAY.SYS CON=(,,2)

   Add the following commands to your AUTOEXEC.BAT file:

   REM ICELAND SETTINGS
   NLSFUNC
   MODE CON CP PREPARE=((861,850) C:\DOS\EGA2.CPI)
   MODE CON CP SELECT=861
   KEYB IS,,C:\DOS\KEYBRD2.SYS

3. Restart your computer.


1.4  Switching Between Modes on Dual-Mode Keyboards
----------------------------------------------------
MS-DOS 6.21 includes dual-mode keyboard support for Greek and French 
Canadian keyboards. These keyboards allow you to easily switch between 
two different keyboard modes. When your computer starts with the
Greek or French Canadian keyboard, the primary mode is active. 
To switch modes, press the appropriate key combination (listed below).

The key combinations for the Greek keyboard are as follows:
		    
		    Mode description    Key combination      
		    ----------------    ---------------     
  Primary mode      Latin               ALT+RIGHT SHIFT
  Secondary mode    Greek               ALT+LEFT SHIFT
		    
The key combinations for the French Canadian keyboard are as follows:
		    
		    Mode description    Key combination      
		    ----------------    ---------------     
  Primary mode      Latin               CTRL+RIGHT SHIFT
  Secondary mode    Latin II            CTRL+LEFT SHIFT


2. MEMMAKER AND MEMORY MANAGEMENT
=================================

2.1 Intel Expanded-Memory Driver (EMM.SYS)
------------------------------------------
If you use Intel's EMM.SYS driver with Aboveboard, use EMM.SYS
version 4.0 revision E if you an ISA system, or EMM.SYS version 4.0
revision D if you have an MCA or other system. Contact Intel for a
free upgrade.

2.2 Running MemMaker on a Computer with PC-NFS
----------------------------------------------
If you use PC-NFS network software, carry out the following procedure
before you run MemMaker:

1. Open your MEMMAKER.INF file by using any text editor. This file is
   in the directory that contains your MS-DOS files.

2. Add the following line to the file:

   *NET

3. Save the file, and then run MemMaker.

2.3 You have a Super VGA display and want to conserve memory.
-------------------------------------------------------------

If you use Microsoft Windows on an 80386 computer with extended
memory and a Super VGA display, you can use the MONOUMB.386 file, in
conjunction with MemMaker, to conserve conventional memory for
running programs.

To conserve memory if you have a Super VGA display:

1. Open your Windows SYSTEM.INI file, and find the [386Enh] section.

2. Add a DEVICE command for the MONOUMB.386 file, which is located
   in your MS-DOS directory. For example, if your MS-DOS files are in
   C:\DOS, add the following line to this section:

   DEVICE=C:\DOS\MONOUMB.386

3. Save the file, and restart your computer.
  
4. After your computer starts, run MemMaker by typing MEMMAKER at the
   command prompt.

5. Choose Custom Setup. On the Advanced Options screen, answer Yes to
   the question "Use monochrome region (B000-B7FF) for running programs?"
  
   Follow the instructions on your screen.

2.4 Using MemMaker with IBM LAN
-------------------------------
Before you run MemMaker, you might need to make adjustments to the
parameters specified for your IBM LAN support driver, DXMC0MOD.SYS. In
your CONFIG.SYS file, make sure that the DEVICE command that loads
DXMC0MOD.SYS includes one of the following before you run MemMaker:

o The first three parameters, as in the following example:

  DEVICE=C:\DXMC0MOD.SYS 400000000001,D800,1

o No parameters, as in the following example:

  DEVICE=C:\DXMC0MOD.SYS

o Some parameters and enough commas to fill in the first three
  parameters, as in the following example:

  DEVICE=C:\DXMC0MOD.SYS 400000000001,,

2.5 MemMaker and Adaptec SCSI devices
-------------------------------------
MemMaker is compatible with Adaptec SCSI devices. However, if you use
the ASPI4DOS.SYS driver to support your SCSI device, MemMaker by default
will exclude this driver from the optimization process. If you don't
use the SCSI device as your startup or boot drive, you can include the
ASPI4DOS.SYS driver in the optimization process. To do so, remove the
^ASPI4DOS entry in the MEMMAKER.INF file, and then run MemMaker.

2.6 Using MemMaker on a computer with PC Tools or PC-DOS RAMBoost
-----------------------------------------------------------------
You can use MemMaker or RAMBoost with MS-DOS, but not both at the
same time. MemMaker will prevent RAMBoost from loading, but not
remove its DEVICE= command from your CONFIG.SYS.

2.7 EMM386 detects an error in an application
---------------------------------------------
If EMM386 displays a message such as "EMM386 has detected error
#12 in an application," this indicates that the processor
has reported an exception error to EMM386. An exception error
typically occurs when an application gives the processor an
instruction under invalid or unexpected conditions. In most cases,
these errors are related to a specific program. If you are receiving
an error that does not occur with any particular application, the
error might be caused by a device driver or a memory-resident
(terminate-and-stay-resident) program.

To avoid these errors:

  o  Try to identify the program involved. One way to do this is
     to see if the error occurs when the program is not running.
     If you suspect a memory-resident program or device driver,
     try bypassing it when your computer starts.

  o  Try disabling EMM386. If a particular application is to blame,
     disabling EMM386 might allow that application to generate an
     error message. Disabling EMM386 might also change
     your memory configuration so that the error no longer occurs.

  o  Try changing the order in which you load device drivers and
     memory-resident programs. This might help because some
     errors occur only under specific memory conditions.

  o  If error 12 is occurring, this indicates that a stack is being used
     incorrectly. Try adding the following command to your CONFIG.SYS
     file:

	STACKS=18,512

  o  If error 13 is occurring, the program may be trying to use protected
     mode without cooperating with EMM386. You may need to obtain a
     VCPI-compliant version of the program, or not load EMM386 when
     using this application.

2.8  MemMaker no longer aggressively scans upper memory by default
------------------------------------------------------------------
By default, the MS-DOS 6.21 version of MemMaker does not scan upper
memory aggressively. Instead, the MemMaker option "Scan the upper 
memory area aggressively?" is set to No, and MemMaker limits its search 
for available UMBs to memory addresses C600 through EFFF. In contrast,
the MS-DOS 6 version of MemMaker did scan upper memory aggressively 
by default: in addition to scanning memory in the C600-EFFF range, 
it also scanned addresses in the range F000 through F7FF. 

To make more memory available for running programs, run MemMaker in 
Custom mode and change the "Scan the upper memory area aggressively?" 
option to Yes. (Note that, on some computers, putting UMBs in this 
range prevents the computer from starting properly.)

Note: If you last ran MemMaker with the "Scan the upper memory
      area aggresively" option set to Yes, then the next time
      you run MemMaker, it leaves that option set to Yes.

2.9 Additional MemMaker Troubleshooting Information
---------------------------------------------------
If you tried the troubleshooting procedures in the chapter "Making
More Memory Available," and you were referred to this file,
determine if one of the following conditions applies to your 
computer:

o If your computer uses an Adaptec controller card, you might not be
  able to use EMM386 unless you have the ADAPTEC.SYS device driver.
  To obtain the device driver, contact Adaptec or your user-group
  bulletin board (BBS) on the Association of PC User User Groups
  (APCUG) network.

o If your computer uses an SCSI (small computer system interface)
  hard disk or other device, or an EDSI (enhanced system device
  interface), or an MCI (Micro Channel Architecture) device, you
  might need to use double-buffering with EMM386.EXE. For more
  information about adding double-buffering, restart your computer
  with EMM386.EXE, and then type HELP DOUBLE-BUFFERING at the 
  command prompt.


3. WINDOWS
==========

3.1 Your computer uses a Windows 3.0 permanent swap file.
---------------------------------------------------------
If your computer uses a Windows 3.0 permanent swap file, run
the SPATCH.BAT program to make the swap file compatible with MS-DOS 6.21
To do so, carry out the following procedure:

1. Copy the SPATCH.BAT file to your hard disk. To determine the location of
   the file on the Setup disks, view the PACKING.LST file on Setup Disk
   1.

2. Type the following at the command prompt:

   SPATCH [DRIVE]:[PATH]SWAPFILE.EXE
  
   For the DRIVE and PATH parameters, specify the location of
   your SWAPFILE.EXE file.

3. Follow the instructions on your screen.

   The program modifies the SWAPFILE.EXE for use with MS-DOS 6.21
   and saves a backup copy as SWAPFILE.SAV. After you have confirmed
   the file works correctly, you can delete the SWAPFILE.SAV file.


4. HARDWARE COMPATIBILITY WITH MS-DOS
=====================================

4.1 Hardcard
------------
For Hardcard information, see the following:

a) Hardcard II

   If you can't use Plus Development Hardcard II or Hardcard
   II XL when running EMM386.EXE, specify the exclude (x=)
   switch to prevent EMM386 from conflicting with the card's
   BIOS address.

   To configure EMM386, run MemMaker.

b) Hardcard 40 or Passport

   If you are using Hardcard 40 or a Passport removable
   disk, and you have a DEVICE command in your CONFIG.SYS file
   for PLUSDRV.SYS, disable or remove the DEVICE command.
   Then run MS-DOS 6.21 Setup. After Setup is complete, reenable or
   restore the DEVICE command for PLUSDRV.SYS. Make it the last line
   in the file.


5. MICROSOFT PROGRAMS
=====================

5.1 Microsoft Anti-Virus
------------------------
Before cleaning a program file, make sure you have a backup copy of it.
If you clean a program file, and the program is corrupted, reinstall the
program. If Anti-Virus again detects a virus, there is a chance the
detection is in error; contact your software vendor to determine if an
updated version of the program is available.

5.2 Running Microsoft Backup for MS-DOS under Windows
-----------------------------------------------------
You should not run Backup for MS-DOS while Windows is running. However,
if you do, and if your system is not configured correctly, Backup
might display the following symptoms:

o Backup appears to stop running--for example, the clock runs, but
  there is no disk activity.

o Backup reports problems while testing the second floppy disk during
  the compatibility test. For example, it might display a "Diskette
  not properly seated" message or ask for Disk 1 repeatedly.

o Windows displays a message that the DMA buffer size needs to be
  increased.

o Backup quits unexpectedly.

You can correctly configure your system by carrying out the following
procedure.

1. Open your SYSTEM.INI file, and add a DMABufferSize=32 line to the
   [386Enh] section.

2. When you run Backup, make sure that you specify with the Settings
   command from the Control menu that Backup run with the Exclusive
   and Full Screen options.

5.3  Backup for Windows stops running at the end of the compatibility test
--------------------------------------------------------------------------
If Backup for Windows stops running at the end of the Compatibility
Test, you might be loading an incompatible third-party backup driver
in your SYSTEM.INI file. Carry out the following procedure.

NOTE  This procedure disables your third-party backup program.

1. Open your SYSTEM.INI file, and locate the [386Enh] section.

2. Determine whether any of the following lines are included in this
   section:

   DEVICE=FASTBACK.386
   DEVICE=VFD.386
   DEVICE=CPBVXD.386
   DEVICE=VIRWT.386

3. If you find any of these lines, add a semicolon (;) to the front
   of the line.

4. Save the file, restart Windows, and run Backup for Windows again.

5.4  Running Microsoft Backup with TI4000 and Gateway NOMAD computers
---------------------------------------------------------------------
To avoid a conflict between the Turbo feature and Microsoft Backup
for Windows or MS-DOS, add a /L0 switch to the DEVICE command in
your CONFIG.SYS that loads the BATTERY.PRO file. Or, before you
run Microsoft Backup, type SETPOWER /L0 at the command prompt.

5.5 Microsoft Defragmenter
--------------------------
If you received the "Insufficient Memory" message from Microsoft
Defragmenter, use the MEM command to determine how much conventional,
upper, and extended (XMS) memory is available. In addition to using
all available conventional memory, Defragmenter can make use of up
to 384K of extended memory and 12K of upper memory.

To increase available memory, carry out the procedures in "An MS-DOS
program displays an out-of-memory message" in the chapter "Diagnosing
and Solving Problems" in the MICROSOFT MS-DOS 6 USER'S GUIDE.

If less than 384K of extended memory is available, carry out
the procedures in "Freeing Extended Memory" in the "Making More
Memory Available" chapter in the MICROSOFT MS-DOS 6 USER'S GUIDE.


6. THIRD-PARTY PROGRAMS
=======================

6.1 4DOS and NDOS
-----------------
4DOS and NDOS are compatible with MS-DOS 6.21.  However, to use some of the
new features in MS-DOS 6.21 (such as MemMaker, the LOADHIGH /L switch,
and the ability to bypass startup commands), contact JP Software to 
obtain 4DOS 4.02 or later, or Symantec to obtain Norton Utilities 7.0 
or later.

If you use multiple configurations, 4DOS or NDOS will not automatically
run your AUTOEXEC.BAT file unless you include a /P on the SHELL line in
your CONFIG.SYS file.

To use MS-DOS 6.21 Help instead of 4DOS or NDOS Help, start it by using
COMMAND /C HELP, or define a 4DOS or NDOS alias to run HELP.COM from
your MS-DOS 6.21 directory.

6.2 Above Board 286 and Above Board Plus Installation
    Programs
-----------------------------------------------------
Do not use an Above Board installation program dated May 1989
or earlier until you disable programs that use extended memory,
such as SMARTDrive or RAMDrive. You might lose data if you leave
these programs enabled. After you have installed Above Board,
you can reenable these programs.

6.3 CodeView
-----------
CAUTION  Using versions 3.0 to 3.13 of the CodeView CV.EXE
file may cause data loss if your system has an 80386 memory
manager (such as EMM386.EXE) and device drivers or programs
that use extended memory. To determine which version you
have, type CV.EXE at the command prompt.

6.4 Colorado Tape Backup
------------------------
If you receive a message that you have two versions of the
VFINTD.386 file loaded, you probably need to edit your
SYSTEM.INI file. To do so, carry out the following procedure:

1. Open your SYSTEM.INI file and locate the [386Enh] section.
   You should see two lines similar to the following:

   DEVICE=C:\TAPE\CMSDTAPE.386
   DEVICE=C:\DOS\VFINTD.386

2. If you plan to use your Colorado Tape Backup program, add a semi-
   colon (;) before the DEVICE command for the VFINTD.386 file. If you
   plan to use Microsoft Backup, add a semi-colon before the DEVICE
   command for the CMSDTAPE.386 file.

3. Save the file, and restart Windows.

6.5 Fastback Plus
-----------------
If you have a version of Fifth Generation Systems Fastback Pluse earlier
than 3.0, use the LOADFIX command before running Fastback Plus or the
Fastback Plus installation program to ensure that you don't lose data. To
do so, type the following at the command prompt:

LOADFIX FB.EXE

or

LOADFIX FBINSTAL.EXE

6.6 Norton Desktop for Windows 2.0
----------------------------------
Setup adds a second Tools menu which contains Microsoft Backup and
Antivirus commands (if you installed these Windows programs).

6.7 PC Tools
------------
If PC Shell does not show all of the files or directories on your drive, 
quit PC Shell immediately and contact Central Point Software for an update. 

CAUTION: Do not attempt to use PC Shell on that drive; severe data 
	 loss might occur. 

The FORMAT command of PC Tools version 7.1 conflicts with
MS-DOS 6.21. Use the FORMAT command that comes with MS-DOS 6.21.

