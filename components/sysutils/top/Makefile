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
# Copyright (c) 2011, 2013, Oracle and/or its affiliates. All rights reserved.
# Copyright (c) 2018, Michal Nowak
#

BUILD_BITS= 64

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		top
COMPONENT_VERSION=	3.8beta1
IPS_COMPONENT_VERSION =	3.8
HUMAN_VERSION=		$(COMPONENT_VERSION)
COMPONENT_SUMMARY=	provides a rolling display of top cpu using processes
COMPONENT_PROJECT_URL=	https://sourceforge.net/projects/unixtop/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:6c683e9cb092078cbc1b2233b15fa8bd3d35a00874e6ba27cf54370d1d64fa4d
COMPONENT_ARCHIVE_URL=	https://sourceforge.net/projects/unixtop/files/unixtop/$(COMPONENT_SRC)/$(COMPONENT_ARCHIVE)
COMPONENT_CLASSIFICATION=	Applications/System Utilities
COMPONENT_FMRI=		diagnostic/top
COMPONENT_LICENSE=	BSD, Apache v2.0

TEST_TARGET=		$(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

# viewpathing support in the build is broken in the 'install' target
COMPONENT_PRE_CONFIGURE_ACTION = ($(CLONEY) $(SOURCE_DIR) $(@D))

CONFIGURE_OPTIONS += --disable-dualarch

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
