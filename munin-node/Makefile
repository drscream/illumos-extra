#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License, Version 1.0 only
# (the "License").  You may not use this file except in compliance
# with the License.
#
# You can obtain a copy of the license at COPYING
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at COPYING.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#
# Copyright (c) 2014, SkyLime.  All rights reserved.
#

VER =	munin-2.0.19

include ../Makefile.defs

PATCHES =	Patches/*

include ../Makefile.targ

all:
	-rm -rf $(VER.32) $(OBJ.32) 
	mkdir -p .unpack32
	gtar x -C .unpack32 $(TARBALL_COMPRESS) --no-same-owner -f $(TARBALL)
	$(APPLY_PATCHES.32)
	mv -f .unpack32/$(VER) ./$(VER.32)
	-rmdir .unpack32
	(cd $(VER.32); DESTDIR=$(DESTDIR) $(MAKE))

install: all
	(cd $(VER.32); DESTDIR=$(DESTDIR) $(MAKE) install-common-prime install-node-prime install-plugins-prime)
