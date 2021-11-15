Compile
=======

Prerequisites
-------------

-  `DOSBox <https://www.dosbox.com/>`__ - DOS emulator which we will
   use to compile the game inside.
-  `4DOS <https://www.4dos.info/v4dos.htm#751>`__ - Command line
   interpreter, which supports the ``copy`` command with binary
   inputs and output.
-  Watcom 10 compiler - For compiling C sources and running MAKEFILEs
-  MASM (Microsoft Macro Assembler) 6.0 - For compiling ASM sources

Getting prerequisites and sources
---------------------------------

DOSBox and 4DOS are freely available. For getting Watcom 10 and MASM
6.0, you need to search the internet. Note that we did not manage to
build the game with Open Watcom. Also, for some reason the MASM version
6.11 compiler did run very slowly in the DOSBox, so it was basically
unusable. We had to use the version 6.0.

All directories and files will placed in the ``~/lba-hacking`` directory
on the host machine. Feel free to change this path, but then adjust the
DOSBox configuration below correspondingly. This directory will be
mounted to ``C:`` in DOSBox.

-  Extract 4DOS into ``4dos``.
-  Extract Watcom and MASM installers into ``install``. These will be
   needed to be installed.
-  Clone https://github.com/2point21/lba1-classic-community into
   ``lba``.

The dir structure at this point should like something like this:

::

   ~/lba-hacking
   ├── 4dos
   ├── install
   │   ├── masm
   │   └── watcom
   └── lba

DOSBox configuration
--------------------

Change the ``autoexec`` section of you DOSBox configuration like below.
The configuration path of DOSBox is usually shown when you start it.

::

   [autoexec]
   mount C ~/lba-hacking

   PATH c:\watcom\binw;c:\masm\bin;%PATH%
   set INCLUDE=c:\watcom\h;c:\lba\lib386
   set WATCOM=c:\watcom
   set EDPATH=c:\watcom\eddat
   set WIPFC=c:\watcom\wipfc

   C:
   C:\4DOS\4DOS.COM

Install tools
-------------

-  Launch DOSBox (e.g. with ``dosbox``).
-  On the first run, 4DOS will prompt some configuration values.
-  Install Watcom by running ``C:\INSTALL\WATCOM\SETUP.EXE`` and
   following the instructions. Leave the default installation path
   ``C:\WATCOM``. The step which proposes to modify ``AUTOEXEC.EXE`` and
   ``CONFIG.SYS`` can be skipped.
-  Install MASM by running ``C:\INSTALL\MASM\DISK1\SETUP.EXE``. Leave the
   default installation paths ``C:\MASM\BINB``, etc...

Check the installation by typing in:

-  ``wmake``: this should show the installed Watcom make version; in my
   case 10.5
-  ``wcc386``: this should show the help of the Watcom C compiler; in my
   case 10.5
-  ``ml``: this should show the version of the Microsoft Macro
   Assembler; in my case 6.00

Now we are ready to build the game.

Build
-----

Run inside the DOSBox

::

   cd C:\LBA\LIB386

   cd LIB_3D
   wmake

   cd ..\LIB_MENU
   wmake

   cd ..\LIB_MIDI
   wmake

   cd ..\LIB_MIX
   wmake

   cd ..\LIB_SAMP
   wmake

   cd ..\LIB_SVGA
   wmake

   cd ..\LIB_SYS
   wmake

   cd ..\..\SOURCES
   wmake
   link

The last command will link the ``LBA0.exe``.

Run
---

To run the game, you will need some assets of the original game.

-  copy HQR files,
-  copy ``M_SB16.DLL``, ``S3.DLL``, and ``W_SB16.DLL``,
-  copy ``LBA.CFG``,

into the directory containing ``LBA0.exe``, in our case
``C:\LBA\SOURCES``.

Run

::

   dos4gw LBA0.exe

Enjoy!
