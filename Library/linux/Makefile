#  Make WWW under unix for linux
#

# For W3 distribution, machine type for subdirectories
WWW_MACH = linux

CFLAGS = -g -Wall -DPOSIXWAIT
LFLAGS =
CC = cc

# Directory for installed binary:
BINDIR = /usr/local/bin

# Where is the W3 object library to be installed (not normally done)?
LIBDIR = $(WWW)/Library/Implementation/$(WWW_MACH)

#_________________ OK if normal W3 distribution
# Where is the WWW source root?
WWW = ../..

#  Where should temporary (object) files go?
WTMP = ../..


#
#	WHEN COMPILING WITH DIRECT WAIS SUPPORT:
#
#	Uncomment these six lines (and edit them, if necessary).
#
# WAIS = ../../../freeWAIS
# WAISLIB =  $(WAIS)/bin/client.a $(WAIS)/bin/wais.a
# MATHLIB = -lm
# WAISINC = -I$(WAIS)/include
# WAISCFLAGS = -DHT_DIRECT_WAIS
# HTWAIS = $(WTMP)/Library/$(WWW_MACH)/HTWAIS.o

VC = 2.17
#	Common Makefile for W3 Library Code
#	-----------------------------------
#
#	(c) CERN 1990, 1991 -- see Copyright.html for conditions
#
# This file should be invariant between systems.
#	DEPENDENCIES NOT COMPLETE @@
#
#	make		Compile and link the software (private version)
#	make install	Copy it into the system (implies make)
#	make update	Copy installed version into installed version
#	make uninstall	Unlink installed version from the system
#	make clean	Remove intermediate files
#	make cleanall	Remove intremediate files and products
#	
# Macros required to be defined already for make:
#
# CC		The C compiler
# CFLAGS	Flags for $(CC) -- except the -I which are below
# LFLAGS	Flags for ld
#
# WWW           The WWW source tree directory
#
# Macros needed for make install:
#
# LIBDIR	Directory for installed library
#______________________________________________________________________

#  If this env var is set to something else Some makes will use that instead
SHELL = /bin/sh

#	.h files are distributed but originally are made from the
#	self-documenting hypertext files.

.SUFFIXES: .h .html
.html.h:
#	- chmod +w $*.h
	www -w90 -na -p -to text/x-c $*.html > $*.h
#	chmod -w $*.h

# If this is actually run in a subdirectory,
#
# WWW = ../../..
# WWW = ../..	For [cernlib] build in this directory

WC = $(WWW)/Library
CMN = $(WWW)/Library/Implementation/
VMS = $(CMN)vms
# Where shall we put the objects and built library?

LOB = $(WTMP)/Library/$(WWW_MACH)

# This path, if relative, is taken relative to the directory
# in which this makefile is, not the pwd.  This screws up the 
# recursive invocation
# include $(CMN)Version.make

# This is now done by cat in WWW/All/Implementation/Makefile
# include $(ABS)$(CMN)Version.make

CFLAGS2 = $(CFLAGS) $(WAISCFLAGS) -I$(CMN) $(SOCKS_FLAGS)

CERNLIBBIN = $(WWW)/bin

COMMON = $(LOB)/HTParse.o $(LOB)/HTAccess.o $(LOB)/HTTP.o \
	$(LOB)/HTFile.o	$(LOB)/HTBTree.o $(LOB)/HTFTP.o $(LOB)/HTTCP.o \
	$(LOB)/SGML.o $(LOB)/HTML.o $(LOB)/HTMLPDTD.o $(LOB)/HTChunk.o \
	$(LOB)/HTPlain.o $(LOB)/HTWriter.o $(LOB)/HTFWriter.o \
	$(LOB)/HTMLGen.o $(LOB)/HTTee.o\
	$(LOB)/HTAtom.o $(LOB)/HTAnchor.o $(LOB)/HTStyle.o \
	$(LOB)/HTList.o $(LOB)/HTString.o $(LOB)/HTAlert.o \
	$(LOB)/HTRules.o $(LOB)/HTFormat.o $(LOB)/HTInit.o $(LOB)/HTMIME.o \
	$(LOB)/HTHistory.o $(LOB)/HTNews.o $(LOB)/HTGopher.o \
	$(LOB)/HTTelnet.o $(LOB)/HTWSRC.o $(HTWAIS) \
	$(LOB)/HTAAUtil.o $(LOB)/HTAABrow.o $(LOB)/HTAssoc.o \
	$(LOB)/HTUU.o $(LOB)/HTMulti.o $(LOB)/HTTeXGen.o \
	$(LOB)/HTDirBrw.o $(LOB)/HTDescript.o $(LOB)/HTGuess.o \
	$(LOB)/HTIcons.o $(LOB)/HTError.o $(LOB)/HTErrorMsg.o

CFILES = $(CMN)HTParse.c $(CMN)HTAccess.c $(CMN)HTTP.c $(CMN)HTFile.c \
        $(CMN)HTBTree.c $(CMN)HTMulti.c \
	$(CMN)HTFTP.c   $(CMN)HTTCP.c     $(CMN)SGML.c $(CMN)HTML.c	\
	$(CMN)HTMLPDTD.c \
	$(CMN)HTPlain.c	$(CMN)HTWriter.c  $(CMN)HTFWriter.c \
        $(CMN)HTMLGen.c	$(CMN)HTTee.c	\
	$(CMN)HTChunk.c $(CMN)HTAtom.c   $(CMN)HTAnchor.c $(CMN)HTStyle.c \
	$(CMN)HTList.c  $(CMN)HTString.c $(CMN)HTAlert.c $(CMN)HTRules.c \
	$(CMN)HTFormat.c $(CMN)HTInit.c $(CMN)HTMIME.c $(CMN)HTHistory.c \
	$(CMN)HTNews.c  $(CMN)HTGopher.c $(CMN)HTTelnet.c \
	$(CMN)HTWAIS.c  $(CMN)HTWSRC.c \
	$(CMN)HTAAUtil.c $(CMN)HTAABrow.c $(CMN)HTAssoc.c \
	$(CMN)HTUU.c $(CMN)HTTeXGen.c \
	$(CMN)HTDirBrw.c $(CMN)HTDescript.c $(CMN)HTGuess.c \
	$(CMN)HTIcons.c $(CMN)HTError.c $(CMN)HTErrorMsg.c

HFILES = $(CMN)HTParse.h $(CMN)HTAccess.h $(CMN)HTTP.h $(CMN)HTFile.h \
	$(CMN)HTMulti.h $(CMN)HTBTree.h $(CMN)HTFTP.h $(CMN)HTTCP.h \
	$(CMN)SGML.h $(CMN)HTML.h $(CMN)HTMLPDTD.h $(CMN)HTChunk.h \
	$(CMN)HTPlain.h		$(CMN)HTWriter.h \
	$(CMN)HTFWriter.h 	$(CMN)HTMLGen.h	\
	$(CMN)HTStream.h $(CMN)HTTee.h\
	$(CMN)HTAtom.h $(CMN)HTAnchor.h $(CMN)HTStyle.h \
	$(CMN)HTList.h \
	$(CMN)HTString.h $(CMN)HTAlert.h $(CMN)HTRules.h \
	$(CMN)HTFormat.h $(CMN)HTInit.h \
	$(CMN)HTMIME.h $(CMN)HTHistory.h $(CMN)HTNews.h \
	$(CMN)HTGopher.h \
	$(CMN)HTUtils.h $(CMN)tcp.h $(CMN)HText.h \
	$(CMN)HTTelnet.h \
	$(CMN)HTWAIS.h  $(CMN)HTWSRC.h \
	$(CMN)HTAAUtil.h $(CMN)HTAABrow.h $(CMN)HTAssoc.h \
	$(CMN)HTUU.h $(CMN)HTTeXGen.h \
	$(CMN)HTDirBrw.h $(CMN)HTDescript.h $(CMN)HTGuess.h \
	$(CMN)HTIcons.h $(CMN)HTError.h

SOURCES = $(CFILES) $(HFILES) $(CMN)Version.make \
	$(CMN)CommonMakefile $(CMN)Makefile \
	$(WWW)/README.txt $(WWW)/Copyright.txt $(WWW)/BUILD $(WWW)/Makefile

SPECIFIC = $(WWW)/All/*/Makefile.include $(WWW)/All/Implementation/Makefile* \
	$(VMS)/descrip.mms  $(VMS)/COPYING.LIB $(VMS)/setup.com \
 	$(VMS)/build_multinet.com $(VMS)/build_multinet.com_alpha \
	$(VMS)/multinet.opt $(VMS)/multinet.opt_alpha \
	$(VMS)/build_ucx.com $(VMS)/build_ucx.com_alpha \
	$(VMS)/ucx.opt $(VMS)/ucx.opt_alpha \
	$(VMS)/patchlevel.h $(VMS)/ufc-crypt.h \
	$(VMS)/crypt.c $(VMS)/crypt_util.c \
	$(VMS)/getline.c $(VMS)/getpass.c \
	$(VMS)/HTVMSUtils.h $(VMS)/HTVMSUtils.c \
	$(VMS)/dirent.h $(VMS)/dirent.c $(VMS)/sys_dirent.h

all : inc $(LOB)/libwww.a

#	Library
#
#  On SGI, ranlib is unnecessary and does not exist so we ignore errors
# for that step.
#  On next 3.1 and following, the archive must be deleted before being
#	build, because has ranlib turned it from an archive of fat files
#	into a fat file of archives. Next time round, ar(1) is 
#	confused as the .a is now a fat file, not an archive.
#
$(LOB)/libwww.a : $(COMMON)
	- rm $(LOB)/libwww.a
	ar r $(LOB)/libwww.a $(COMMON)
	-ranlib $(LOB)/libwww.a

#	Clean up everything generatable except final products
clean :
	rm $(LOB)/*.o $(LOB)/.created
	-rmdir $(LOB)

#	Clean up everything generatable including final products

cleanall : clean
	rm $(LOB)/libwww.a

#	Install W3 library into system space (not normally necessary)

install : libwww.a
	if [ ! -r $(LIBDIR) ] mkdir $(LIBDIR)
	cp libwww.a $(LIBDIR)/libwww.a
	
uninstall :
	rm $(LIBDIR)/libwww.a

#		Distribution use only:
#		----------------------

#	Needs www version 2.4 or later to do this
inc : $(HFILES)
	echo Include files generated from hypertext.

binary : /mnt/www0/pub/www/bin/$(WWW_MACH)/libwww_$(VC).a
	echo FTP archive binary Libray $(VC) for $(WWW_MACH) up to date.


/mnt/www0/pub/www/bin/$(WWW_MACH)/libwww_$(VC).a : libwww.a
	-mkdir /mnt/www0/pub/www/bin/$(WWW_MACH)
	cp libwww.a /mnt/www0/pub/www/bin/$(WWW_MACH)/libwww_$(VC).a

#	Source Distribution:

distribute : /mnt/www0/pub/www/README.txt /mnt/www0/pub/www/Copyright.txt
	(cd $(WWW)/..; WWW=WWW ABS=`pwd`/ make $(MFLAGS) \
	-f WWW/Library/Implementation/Version.make \
	-f WWW/Library/Implementation/CommonMakefile \
	/mnt/www0/pub/www/src/WWWLibrary_$(VC).tar.Z)
	(cd ../Implementation; cvs tag \
	`sed -e 's/VC = /v/' Version.make | sed -e 's?\.?/?'` )
	echo Distribution of Library version $(VC) up to date.

/mnt/www0/pub/www/src/WWWLibrary_$(VC).tar.Z : $(SOURCES)
	tar cvf /mnt/www0/pub/www/src/WWWLibrary_$(VC).tar \
	    $(SOURCES) \
	    $(SPECIFIC) \
	    $(WWW)/All \
	    $(CMN)*.html
	compress -f /mnt/www0/pub/www/src/WWWLibrary_$(VC).tar

#	Hypertext supplied in text format
#	---------------------------------

$(WWW)/README.txt : $(WWW)/../README.html
	www -n -p66 http://info.cern.ch/hypertext/README.html \
		> $(WWW)/README.txt
/mnt/www0/pub/www/README.txt : $(WWW)/README.txt
	cp $(WWW)/README.txt /mnt/www0/pub/www/README.txt

$(WWW)/Copyright.txt : $(WWW)/../Copyright.html
	www -n -p66 http://info.cern.ch/hypertext/Copyright.html \
		> $(WWW)/Copyright.txt
/mnt/www0/pub/www/Copyright.txt : $(WWW)/Copyright.txt
	cp $(WWW)/Copyright.txt /mnt/www0/pub/www/Copyright.txt

# 			Common code
#			-----------

#	Directory for object files - .created checks it exists

OE = $(LOB)/.created
$(OE) :
	if [ ! -r $(WTMP) ] ; then mkdir $(WTMP); else echo OK ; fi
	if [ ! -r $(WTMP)/Library ] ; then mkdir $(WTMP)/Library; else echo OK ; fi
	if [ ! -r $(WTMP)/Library/$(WWW_MACH) ] ; \
		then mkdir $(WTMP)/Library/$(WWW_MACH); else echo OK ; fi
	touch $@

$(LOB)/HTList.o : $(OE) $(CMN)HTList.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTList.c

$(LOB)/HTAnchor.o : $(OE) $(CMN)HTAnchor.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTAnchor.c

$(LOB)/HTFormat.o : $(OE) $(CMN)HTFormat.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTFormat.c

$(LOB)/HTGuess.o : $(OE) $(CMN)HTGuess.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTGuess.c

$(LOB)/HTInit.o : $(OE) $(CMN)HTInit.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTInit.c

$(LOB)/HTMIME.o : $(OE) $(CMN)HTMIME.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTMIME.c

$(LOB)/HTHistory.o : $(OE) $(CMN)HTHistory.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTHistory.c

$(LOB)/HTNews.o : $(OE) $(CMN)HTNews.c $(CMN)HTUtils.h $(CMN)HTList.h\
	 $(CMN)HTMLPDTD.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTNews.c

$(LOB)/HTGopher.o : $(OE) $(CMN)HTGopher.c $(CMN)HTUtils.h $(CMN)HTList.h \
	 $(CMN)HTMLPDTD.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTGopher.c

$(LOB)/HTTelnet.o : $(OE) $(CMN)HTTelnet.c $(CMN)HTUtils.h $(CMN)HTTelnet.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTTelnet.c

$(LOB)/HTStyle.o : $(OE) $(CMN)HTStyle.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTStyle.c

$(LOB)/HTAtom.o : $(OE) $(CMN)HTAtom.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTAtom.c

$(LOB)/HTChunk.o : $(OE) $(CMN)HTChunk.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTChunk.c

$(LOB)/HTString.o : $(OE) $(CMN)HTString.c $(CMN)HTUtils.h $(CMN)Version.make
	$(CC) -c -o $@ $(CFLAGS2) -DVC=\"$(VC)\" $(CMN)HTString.c

$(LOB)/HTAlert.o : $(OE) $(CMN)HTAlert.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTAlert.c

$(LOB)/HTRules.o : $(OE) $(CMN)HTRules.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTRules.c

$(LOB)/SGML.o : $(OE) $(CMN)SGML.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)SGML.c

$(LOB)/HTML.o : $(OE) $(CMN)HTML.c $(CMN)HTUtils.h $(CMN)HTMLPDTD.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTML.c

$(LOB)/HTMLGen.o : $(OE) $(CMN)HTMLGen.c $(CMN)HTUtils.h $(CMN)HTMLPDTD.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTMLGen.c

$(LOB)/HTTeXGen.o : $(OE) $(CMN)HTTeXGen.c $(CMN)HTUtils.h $(CMN)HTMLPDTD.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTTeXGen.c

$(LOB)/HTMLPDTD.o : $(OE) $(CMN)HTMLPDTD.c $(CMN)SGML.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTMLPDTD.c

$(LOB)/HTPlain.o : $(OE) $(CMN)HTPlain.c $(CMN)HTPlain.h $(CMN)HTStream.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTPlain.c

$(LOB)/HTTee.o : $(OE) $(CMN)HTTee.c $(CMN)HTTee.h $(CMN)HTStream.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTTee.c

$(LOB)/HTWAIS.o : $(OE) $(CMN)HTWAIS.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(WAISINC) $(CMN)HTWAIS.c

$(LOB)/HTWSRC.o : $(OE) $(CMN)HTWSRC.c $(CMN)HTUtils.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTWSRC.c

$(LOB)/HTWriter.o : $(OE) $(CMN)HTWriter.c $(CMN)HTWriter.h $(CMN)HTStream.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTWriter.c

$(LOB)/HTFWriter.o : $(OE) $(CMN)HTFWriter.c $(CMN)HTFWriter.h $(CMN)HTStream.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTFWriter.c


#	Access Authorization

$(LOB)/HTAAUtil.o : $(OE) $(CMN)HTAAUtil.c $(CMN)HTAAUtil.h \
	 $(CMN)HTUtils.h $(CMN)HTString.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTAAUtil.c

$(LOB)/HTAABrow.o : $(OE) $(CMN)HTAABrow.c $(CMN)HTAABrow.h \
	 $(CMN)HTAAUtil.h $(CMN)HTUU.h \
	 $(CMN)HTUtils.h $(CMN)HTString.h \
	 $(CMN)HTParse.h $(CMN)HTList.h $(CMN)HTAlert.h \
	 $(CMN)HTAssoc.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTAABrow.c

$(LOB)/HTAssoc.o : $(OE) $(CMN)HTAssoc.c $(CMN)HTAssoc.h \
	$(CMN)HTUtils.h $(CMN)HTString.h $(CMN)HTList.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTAssoc.c

$(LOB)/HTUU.o : $(OE) $(CMN)HTUU.c $(CMN)HTUU.h $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTUU.c


#	Communications & Files

$(LOB)/HTTP.o : $(OE) $(CMN)HTTP.c $(CMN)HTUtils.h $(CMN)HTAABrow.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTTP.c

$(LOB)/HTTCP.o : $(OE) $(CMN)HTTCP.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTTCP.c

$(LOB)/HTFile.o : $(OE) $(CMN)HTFile.c $(CMN)HTUtils.h \
	 $(CMN)HTMLPDTD.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTFile.c

$(LOB)/HTDirBrw.o : $(OE) $(CMN)HTDirBrw.c $(CMN)HTDirBrw.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTDirBrw.c

$(LOB)/HTIcons.o : $(OE) $(CMN)HTIcons.c $(CMN)HTIcons.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTIcons.c

$(LOB)/HTDescript.o : $(OE) $(CMN)HTDescript.c $(CMN)HTDescript.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTDescript.c

$(LOB)/HTMulti.o : $(OE) $(CMN)HTMulti.c $(CMN)HTUtils.h \
	 $(CMN)HTFile.h $(CMN)HTMulti.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTMulti.c

$(LOB)/HTBTree.o : $(OE) $(CMN)HTBTree.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTBTree.c

$(LOB)/HTFTP.o : $(OE) $(CMN)HTFTP.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTFTP.c

$(LOB)/HTAccess.o : $(OE)  $(CMN)HTAccess.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTAccess.c

$(LOB)/HTParse.o : $(OE) $(CMN)HTParse.c $(CMN)HTUtils.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTParse.c

$(LOB)/HTError.o : $(OE) $(CMN)HTError.c $(CMN)HTError.h
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTError.c

$(LOB)/HTErrorMsg.o : $(OE) $(CMN)HTErrorMsg.c
	$(CC) -c -o $@ $(CFLAGS2) $(CMN)HTErrorMsg.c
