######################################################################

Title:  UIF2ISO
Author: Luigi Auriemma
e-mail: aluigi@autistici.org
web:    aluigi.org

UIF2ISO homepage:
        http://aluigi.org/mytoolz.htm#uif2iso

######################################################################

1) Introduction
2) Usage on Windows
3) Usage on *nix/MacOSX
4) Features and known bugs
5) Technical info about the format
6) Comments about the UIF format

######################################################################

===============
1) Introduction
===============

UIF2ISO is an open source command-line/GUI tool for converting single
and multipart UIF images to the original ISO format.

The UIF image (Universal Image Format) in fact is just a compressed
CD/DVD image which can be created through the commercial program
MagicISO.


######################################################################

===================
2) Usage on Windows
===================

Using UIF2ISO on Windows is really a joke, just double click on
UIF2ISO.exe and the tool will open a DOS-like window which contains
all the needed informations about the status of conversion, then you
will need to choose the input UIF file you want to convert and
subsequently the name of the output file you want to create.
Note that the correct extension (ISO, NRG or BIN/CUE) is automatically
choosed by the tool depending by the input UIF file.

If you want to use the tool from the command-line, so specifying the
input and output files manually as in the older versions of the tool,
you can do it too since UIF2ISO automatically recognizes if it has
been launched from the console (cmd.exe) or through double-click.
Just specify the input UIF file and the output ISO file you want to
create like in the examples of the subsequent section.

Remember that you can also associate the UIF extension to UIF2ISO, so
when you will double-click on these files UIF2ISO will popup and will
allow you to choose the output file immediately or you can also
drag'n'drop the UIF file directly on UIF2ISO.EXE.

Note that UIF2ISO is a stand-alone program, so all you need to have is
just UIF2ISO.EXE and you can place it everywhere you want.


######################################################################

=======================
3) Usage on *nix/MacOSX
=======================

Compile the source code using 'make', this will generate the UIF2ISO
executable.
If you want to install it type 'make install' or just copy the
executable where you want since it's the only file you need.

The only requirements for compiling and using UIF2ISO are zlib and
OpenSSL (apt-get install zlib1g zlib1g-dev libssl-dev).

Using it then it's simple, just specify the input file and the ISO
file you want to create like the following example:

  uif2iso "my file.uif" output.iso


######################################################################

==========================
4) Features and known bugs
==========================

The tool supports password/encryption, little/big endian architectures
and should work on many platforms (Windows, Linux, MacOS, *BSD, Amiga
and others).

The NRG file (compressed UIF) created by MagicISO is invalid so
although my tool tries to fix some fields and generates an additional
CUE file is possible that the resulted image isn't fully recognized by
the burning/mounting program you want to use.

A known micro-bug is that on Windows 95/98/ME works only the so
called GUI version because the method I use to know if the program has
been launched from the console or through double-click is not
compatible with this OS, anyway this is not a problem since the 99% of
the Windows users don't like the command-line 8-)

I'm available for any comment or feedback, so if you find a
compatibility problem with a specific UIF image (and you are sure that
the image is perfect) send me a mail.


######################################################################

==================================
5) Technical info about the format
==================================

UIF2ISO is open source so there is nothing better than its source code
for explaining in detail this file format.

In short UIF is a compressed disk image which can be derived by 3
types of input images:
- ISO: only the classical data
- BIN/CUE: data, audio or mixed content
  the UIF file contains a BLMS section with raw CUE informations
  (UIF2ISO uses them to generate the relative CUE file) and a BLSS
  field containing the original CUE file used by who created the UIF
- NRG: disk image in Nero v2 format
  unfortunately for some reasons which I don't know the "UIFed" NRG
  image generated by MagicISO is invalid (these images don't work with
  other programs included Nero which is the creator of the NRG
  format!) and although my UIF2ISO fixes some of these fields is still
  possible that with some type of images the fixed NRG could not work
  since not 100% compatible.
  Another work-around I have adopted is the generation of an
  additional CUE file derived from the NRG one which in my test worked
  perfectly with data, audio and mixed CDs and partially with CD
  extra.


######################################################################

================================
6) Comments about the UIF format
================================

I don't like and don't approve the UIF format because it's proprietary
and doesn't give benefits.
What you can do with UIF can be done better with ZIP or 7zip without
the need to be forced to buy a software like MagicISO only for burning
an image.

Ok exists my tool which can do the job but this is not a valid reason
to continue to use this useless format.

So if you want to create a CD/DVD image, DO NOT USE UIF!


