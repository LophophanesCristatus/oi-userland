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
# Copyright (c) 2024 Geoff Weiss
#

BUILD_STYLE= meson
USE_DEFAULT_TEST_TRANSFORMS = yes

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=         drawing
COMPONENT_VERSION=      1.0.2
COMPONENT_REVISION=	1
COMPONENT_SUMMARY=      Simple image editor
COMPONENT_PROJECT_URL=  https://maoschanz.github.io/drawing/
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_VERSION).tar.gz
COMPONENT_ARCHIVE_HASH= sha256:539e7e28fe4db96cfedd4477e217d5d48b9422ad8c98f33d8ae46120b2d5738b
COMPONENT_ARCHIVE_URL=  https://github.com/maoschanz/drawing/archive/refs/tags/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=         image/editor/drawing
COMPONENT_CLASSIFICATION=Applications/Graphics and Imaging
COMPONENT_LICENSE=	GPL-3.0-only
COMPONENT_LICENSE_FILE= LICENSE

include $(WS_MAKE_RULES)/common.mk

# GNU msgfmt is needed
PATH= $(PATH.gnu)

# Not detected dependencies 
PYTHON_REQUIRED_PACKAGES += library/python/pycairo
REQUIRED_PACKAGES += library/desktop/gtk3

# Auto-generated dependencies
PYTHON_REQUIRED_PACKAGES += library/python/pygobject
PYTHON_REQUIRED_PACKAGES += runtime/python
