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
# Copyright (c) 2016 Jim Klimov
# Copyright (c) 2020 Andreas Wacknitz
#

USE_PARALLEL_BUILD= yes
DROP_STATIC_LIBRARIES= yes
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		SDL2
COMPONENT_VERSION=	2.32.0
COMPONENT_SUMMARY=	libsdl2 - Simple DirectMedia Layer 2.0
COMPONENT_PROJECT_URL=	https://www.libsdl.org
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:f5c2b52498785858f3de1e2996eba3c1b805d08fe168a47ea527c7fc339072d0
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/release/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI =	library/sdl2
COMPONENT_CLASSIFICATION =	System/Libraries
COMPONENT_LICENSE=	ZLIB
COMPONENT_LICENSE_FILE=	LICENSE.txt

TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

PATH= $(PATH.gnu)

CFLAGS += $(XPG6MODE)

COMPONENT_PREP_ACTION= ( cd $(@D) && $(CONFIG_SHELL) autogen.sh );

CONFIGURE_OPTIONS += --disable-rpath
CONFIGURE_OPTIONS += --enable-year2038
CONFIGURE_OPTIONS += --enable-static=no

# Manually added build dependencies
REQUIRED_PACKAGES += library/libsamplerate

# Auto-generated dependencies
REQUIRED_PACKAGES += shell/ksh93
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
