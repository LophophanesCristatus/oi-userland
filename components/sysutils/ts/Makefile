#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"). You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2014 Josef 'Jeff' Sipek <jeffpc@josefsipek.net>
#

BUILD_STYLE= justmake
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		ts
COMPONENT_VERSION=	1.0.3
COMPONENT_SUMMARY=	task spooler - a Unix batch system
COMPONENT_PROJECT_URL= https://vicerveza.homeunix.net/~viric/soft/ts/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:fa833311543dc535b60cb7ab83c64ab5ee31128dbaaaa13dde341984e542b428
COMPONENT_ARCHIVE_URL=	https://vicerveza.homeunix.net/~viric/soft/ts/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		utility/ts
COMPONENT_CLASSIFICATION=	System/Administration and Configuration
COMPONENT_LICENSE=	GPLv2+
COMPONENT_LICENSE_FILE=	COPYING

include $(WS_MAKE_RULES)/common.mk

COMPONENT_BUILD_ENV  = CC=$(CC)
COMPONENT_BUILD_ENV += CFLAGS="$(CFLAGS) -pedantic -ansi -Wall"
COMPONENT_BUILD_ENV += LDFLAGS="$(CC_BITS) -lsocket -lnsl"

COMPONENT_INSTALL_ARGS=PREFIX=$(PROTO_DIR)/usr

COMPONENT_TEST_CMD= ./testbench.sh
COMPONENT_TEST_TARGETS=
COMPONENT_TEST_ENV += PATH=$(PROTOUSRBIN):$(USRBINDIR)

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
