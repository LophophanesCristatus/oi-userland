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
# Copyright 2021, 2024, Andreas Wacknitz
#

BUILD_STYLE= justmake
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		sbcl
COMPONENT_VERSION=	2.5.1
COMPONENT_SUMMARY=	sbcl - Steel Bank Common Lisp
COMPONENT_PROJECT_URL=	https://sbcl.sourceforge.io/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC)-source.tar.bz2
COMPONENT_ARCHIVE_HASH=	sha256:4133b36cd16d14d633969c37fd51c2c89a8ea5d6e1611552819d91f71b219f8b
COMPONENT_ARCHIVE_URL=	https://downloads.sourceforge.net/project/sbcl/sbcl/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		runtime/sbcl
COMPONENT_CLASSIFICATION=	Development/Other Languages
COMPONENT_LICENSE=	BSD-PublicDomain
COMPONENT_LICENSE_FILE=	COPYING

TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

COMPONENT_ENV  =	PATH="$(PATH)"
COMPONENT_ENV +=	GNUMAKE=$(GMAKE)
COMPONENT_ENV +=	CC="$(CC)"
COMPONENT_BUILD_ARGS  =	--prefix=$(USRDIR)
COMPONENT_BUILD_ARGS +=	--arch=x86-64
# This is currently --with-sb-thread --with-sb-core-compression
# --with-sb-xref-internals and :sb-after-xc-core as a build feature.
COMPONENT_BUILD_ARGS +=	--fancy

$(BUILD_DIR)/%/.built:	$(SOURCE_DIR)/.prep
	$(RM) -r $(@D) ; $(MKDIR) $(BUILD_DIR)
	$(CP) -a $(SOURCE_DIR) $(@D)
	(cd $(@D) ; $(ENV) $(COMPONENT_ENV) /usr/gnu/bin/sh make.sh $(COMPONENT_BUILD_ARGS))
	(cd $(@D)/doc/manual ; $(ENV) $(COMPONENT_ENV) BUILD_ROOT=$(PROTO_DIR) $(GMAKE) html info)
	$(TOUCH) $@

$(BUILD_DIR)/%/.installed:	$(BUILD_DIR)/%/.built
	(cd $(@D) ; $(ENV) $(COMPONENT_ENV) BUILD_ROOT=$(PROTO_DIR) /usr/gnu/bin/sh install.sh)
	$(TOUCH) $@

$(BUILD_DIR)/%/.tested:		$(BUILD_DIR)/%/.installed
	(cd $(@D)/tests; $(ENV) $(COMPONENT_ENV) BUILD_ROOT=$(PROTO_DIR) /usr/gnu/bin/sh run-tests.sh)

# Pre-installed sbcl is needed to build sbcl
REQUIRED_PACKAGES += runtime/sbcl

# Auto-generated dependencies
REQUIRED_PACKAGES += compress/zstd
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
