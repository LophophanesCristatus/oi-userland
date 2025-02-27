#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2016 Jim Klimov
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=         libmikmod
COMPONENT_VERSION=      3.3.12
COMPONENT_SUMMARY=      MOD file playing library
COMPONENT_CLASSIFICATION=System/Multimedia Libraries
COMPONENT_PROJECT_URL=  https://mikmod.sourceforge.net/
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH= sha256:adef6214863516a4a5b44ebf2c71ef84ecdfeb3444973dacbac70911c9bc67e9
COMPONENT_ARCHIVE_URL=  https://sourceforge.net/projects/mikmod/files/libmikmod/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)/download/
COMPONENT_FMRI=         library/audio/libmikmod
COMPONENT_LICENSE=      LGPLv2
COMPONENT_LICENSE_FILE= COPYING.LIB

include $(WS_MAKE_RULES)/common.mk

# gcc 14 needs XPG6 here
CFLAGS += $(XPG6MODE)
CFLAGS += -std=c99

CONFIGURE_OPTIONS  += --enable-shared
CONFIGURE_OPTIONS  += --disable-static
CONFIGURE_OPTIONS  += --enable-alsa
CONFIGURE_OPTIONS  += --enable-oss
CONFIGURE_OPTIONS  += --enable-sdl2
CONFIGURE_OPTIONS  += --enable-sunaudio
CONFIGURE_OPTIONS  += --enable-pulseaudio
CONFIGURE_OPTIONS  += --enable-openal

COMPONENT_POST_INSTALL_ACTION += ( $(RM) $(PROTOUSRSHAREDIR)/info/dir );

# Manually added build dependencies
REQUIRED_PACKAGES += library/audio/pulseaudio

# Auto-generated dependencies
REQUIRED_PACKAGES += library/audio/openal
REQUIRED_PACKAGES += shell/ksh93
REQUIRED_PACKAGES += system/library
