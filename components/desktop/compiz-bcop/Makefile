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
# Copyright (c) 2014 Alexander Pyhalov
# Copyright (c) 2018 Michal Nowak
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		compiz-bcop
COMPONENT_VERSION=	0.8.18
COMPONENT_REVISION=	1
COMPONENT_SUMMARY=	beryl compiz XML option parser
COMPONENT_PROJECT_URL=	http://www.northfield.ws/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_NAME)-$(COMPONENT_VERSION).tar.xz
COMPONENT_ARCHIVE_HASH=	sha256:59768aa1e01c58fea61848fe7277dc7714e0e0b9d79fd9bbad94262a5c8b63f7
COMPONENT_ARCHIVE_URL=	http://www.northfield.ws/projects/compiz/releases/$(COMPONENT_VERSION)/$(COMPONENT_SRC).tar.xz
COMPONENT_FMRI=		desktop/compiz/bcop
COMPONENT_CLASSIFICATION=Development/Other Languages
COMPONENT_LICENSE=	MIT, LGPLv2.1, GPLv2
COMPONENT_LICENSE_FILE=	COPYING

TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

PATH= $(PATH.gnu)

COMPONENT_PREP_ACTION= ( \
	cd $(@D) && \
	aclocal -I. && \
    autoheader && \
    libtoolize --automake --copy --force && \
	automake -a -f -c && \
	autoconf )

CONFIGURE_OPTIONS += --sysconfdir=$(ETCDIR)
CONFIGURE_OPTIONS += --with-getopt=/usr/gnu/bin/getopt

# Build dependencies
REQUIRED_PACKAGES += desktop/compiz

# Auto-generated dependencies
REQUIRED_PACKAGES += shell/bash
