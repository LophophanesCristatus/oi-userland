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
# Copyright 2011 EveryCity Ltd. All rights reserved.
# Copyright 2019 Michal Nowak
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		ogl-select
COMPONENT_VERSION=	0.5.11
COMPONENT_REVISION=	6
COMPONENT_SUMMARY=	ogl-select - boot time selection of OpenGL vendor files
COMPONENT_PROJECT_URL = https://www.openindiana.org/
COMPONENT_FMRI=		service/opengl/ogl-select
COMPONENT_LICENSE=	MIT
COMPONENT_LICENSE_FILE=	ogl-select.license
COMPONENT_CLASSIFICATION= System/X11


include $(WS_MAKE_RULES)/ips.mk

download:

prep:

build:

install:
	[ -d $(PROTO_DIR) ] || mkdir -p $(PROTO_DIR)

clean:
	$(RM) -r $(BUILD_DIR) $(PROTO_DIR)

# Auto-generated dependencies
REQUIRED_PACKAGES += SUNWcs
REQUIRED_PACKAGES += shell/ksh93
