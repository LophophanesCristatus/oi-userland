#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END

#
# Copyright (c) 2011, 2012, Oracle and/or its affiliates. All rights reserved.
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		hal-cups-utils
COMPONENT_VERSION=	0.6.19
COMPONENT_REVISION=	2
COMPONENT_SUMMARY=	the HAL automatic queue creation plugin module for CUPS
COMPONENT_DESCRIPTION=	hal-cups-utils is a Hardware Abstraction Layer (HAL) plugin module that automatically creates print queues under the Common UNIX Printing System (CUPS) for printers detected by HAL.
COMPONENT_PROJECT_URL=	http://fedorahosted.org/hal-cups-utils/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:f40a7ebd1453d471a8a6bfd8c635708dd739a6160bb661813f936d936ba85618
COMPONENT_ARCHIVE_URL=	ftp://ftp.slackware.org.uk/gsb/gsb-2.28_slackware-13.1/source/l/hal-cups-utils/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		print/cups/hal-cups-utils
COMPONENT_CLASSIFICATION=	System/Printing
COMPONENT_LICENSE=	CUPS License
COMPONENT_LICENSE_FILE=	COPYING

include $(WS_MAKE_RULES)/common.mk

PATCH_LEVEL= 0
USED_PYTHON= $(PYTHON)
ACLOCAL=	/usr/bin/aclocal-1.11
AUTOMAKE=	/usr/bin/automake-1.11

CONFIGURE_ENV += PYTHON=$(USED_PYTHON)

CONFIGURE_OPTIONS += --datarootdir=$(ETCDIR)

# Since we patch Makefile.am, we have to rebuild the autoconf generated files
# Just running automake does not work, since our automake is different from the one
# used by hal-cups-utils maintainer
COMPONENT_PREP_ACTION = ( \
	cd $(@D); \
	ACLOCAL=$(ACLOCAL) AUTOMAKE=$(AUTOMAKE) autoreconf; \
	cd $(SOURCE_DIR); \
	$(PERL) -pi -e 's,^\#!.*?python,\#!$(USED_PYTHON), if $$.==1' systemv/hal_lpadmin ; \
) 


# Manually added build dependencies
PYTHON_REQUIRED_PACKAGES += runtime/python
REQUIRED_PACKAGES += developer/build/automake-111

# Auto-generated dependencies
REQUIRED_PACKAGES += library/print/cups-libs
REQUIRED_PACKAGES += service/hal
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/libdbus
