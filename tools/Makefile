# SPDX-License-Identifier: Zlib
#
# Copyright (c) 2023 Antonio Niño Díaz

STRIP		:= -s
BINMODE		:= 755

MAKE		:= make
INSTALL		:= install

.PHONY: bin2c clean dldipatch dlditool grit install mmutil ndstool

all: bin2c dldipatch dlditool grit mmutil ndstool

bin2c: bin2c/bin2c

bin2c/bin2c:
	$(MAKE) -C bin2c -j`nproc`

grit: grit/grit

grit/grit:
	$(MAKE) -C grit -j`nproc`

dlditool: dlditool/dlditool

dlditool/dlditool:
	$(MAKE) -C dlditool -j`nproc`

dldipatch: dldipatch/dldipatch

dldipatch/dldipatch:
	$(MAKE) -C dldipatch -j`nproc`

mmutil: mmutil/mmutil

mmutil/mmutil:
	$(MAKE) -C mmutil -j`nproc`

ndstool: ndstool/ndstool

ndstool/ndstool:
	$(MAKE) -C ndstool -j`nproc`

INSTALLDIR_ABS	:= $(abspath $(INSTALLDIR))

install: all
	@echo "INSTALLDIR = '$(INSTALLDIR)' (must not be empty)"
	@test $(INSTALLDIR)
	$(INSTALL) -d $(INSTALLDIR_ABS)/tools \
		      $(INSTALLDIR_ABS)/tools/bin2c \
		      $(INSTALLDIR_ABS)/tools/dldi \
		      $(INSTALLDIR_ABS)/tools/dldipatch \
		      $(INSTALLDIR_ABS)/tools/dlditool \
		      $(INSTALLDIR_ABS)/tools/grit \
		      $(INSTALLDIR_ABS)/tools/imgbuild \
		      $(INSTALLDIR_ABS)/tools/mmutil \
		      $(INSTALLDIR_ABS)/tools/ndstool
	$(INSTALL) $(STRIP) -m $(BINMODE) bin2c/bin2c $(INSTALLDIR_ABS)/tools/bin2c/
	$(INSTALL) dldi/r4tfv2.dldi $(INSTALLDIR_ABS)/tools/dldi/
	$(INSTALL) $(STRIP) -m $(BINMODE) dldipatch/dldipatch $(INSTALLDIR_ABS)/tools/dldipatch/
	$(INSTALL) $(STRIP) -m $(BINMODE) dlditool/dlditool $(INSTALLDIR_ABS)/tools/dlditool/
	$(INSTALL) -m $(BINMODE) imgbuild/imgbuild.sh $(INSTALLDIR_ABS)/tools/imgbuild/
	$(INSTALL) $(STRIP) -m $(BINMODE) grit/grit $(INSTALLDIR_ABS)/tools/grit/
	$(INSTALL) $(STRIP) -m $(BINMODE) mmutil/mmutil $(INSTALLDIR_ABS)/tools/mmutil/
	$(INSTALL) $(STRIP) -m $(BINMODE) ndstool/ndstool $(INSTALLDIR_ABS)/tools/ndstool/

clean:
	$(MAKE) -C bin2c clean
	$(MAKE) -C dldipatch clean
	$(MAKE) -C dlditool clean
	$(MAKE) -C grit clean
	$(MAKE) -C mmutil clean
	$(MAKE) -C ndstool clean
