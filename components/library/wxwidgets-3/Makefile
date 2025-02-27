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
# Copyright 2017 Aurelien Larcher
# Copyright 2019 Michal Nowak
#

USE_PARALLEL_BUILD= yes
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=         wxwidgets-3
COMPONENT_MAJOR_VERSION= 3.2
COMPONENT_VERSION=		$(COMPONENT_MAJOR_VERSION).6
COMPONENT_SUMMARY=      wxWidgets - Cross-Platform GUI Library
COMPONENT_PROJECT_URL=  https://www.wxwidgets.org/
COMPONENT_SRC_NAME=     wxWidgets
COMPONENT_SRC=          $(COMPONENT_SRC_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_URL=  https://github.com/wxWidgets/wxWidgets/releases/download/v$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_ARCHIVE_HASH= sha256:939e5b77ddc5b6092d1d7d29491fe67010a2433cf9b9c0d841ee4d04acb9dce7
COMPONENT_FMRI=         library/graphics/$(COMPONENT_NAME)
COMPONENT_CLASSIFICATION=Desktop (GNOME)/Libraries
COMPONENT_LICENSE=      wxWindows Library license
COMPONENT_LICENSE_FILE= docs/licence.txt

TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

CONFIGURE_OPTIONS += --with-gtk=2
CONFIGURE_OPTIONS += --without-gtkprint
CONFIGURE_OPTIONS += --enable-gui
CONFIGURE_OPTIONS += --enable-xrc
CONFIGURE_OPTIONS += --enable-display
CONFIGURE_OPTIONS += --disable-epollloop
CONFIGURE_OPTIONS += --enable-geometry
CONFIGURE_OPTIONS += --enable-graphics_ctx
CONFIGURE_OPTIONS += --enable-mediactrl
CONFIGURE_OPTIONS += --enable-mimetype
CONFIGURE_OPTIONS += --enable-sound
CONFIGURE_OPTIONS += --enable-unicode
CONFIGURE_OPTIONS += --enable-webview
CONFIGURE_OPTIONS += --disable-xlocale
CONFIGURE_OPTIONS += --with-subdirs
CONFIGURE_OPTIONS += --with-expat
CONFIGURE_OPTIONS += --without-gnomevfs
CONFIGURE_OPTIONS += --with-libjpeg=sys
CONFIGURE_OPTIONS += --with-libpng=sys
CONFIGURE_OPTIONS += --with-regex=sys
CONFIGURE_OPTIONS += --with-libtiff=sys
CONFIGURE_OPTIONS += --without-libmspack
CONFIGURE_OPTIONS += --with-opengl
CONFIGURE_OPTIONS += --with-sdl

# Note: We need to uninstall some packages from the encumbered repository before building this as they might be detected and used otherwise:
# pfexec pkg uninstall library/audio/gstreamer1/plugin/bad library/audio/gstreamer1/devtools

# Auto-generated dependencies
REQUIRED_PACKAGES += $(GCC_RUNTIME_PKG)
REQUIRED_PACKAGES += $(GXX_RUNTIME_PKG)
REQUIRED_PACKAGES += $(JPEG_IMPLEM_PKG)
REQUIRED_PACKAGES += image/library/libjpeg-turbo
REQUIRED_PACKAGES += image/library/libpng16
REQUIRED_PACKAGES += image/library/libtiff
REQUIRED_PACKAGES += library/audio/gstreamer1
REQUIRED_PACKAGES += library/audio/gstreamer1/plugin/base
REQUIRED_PACKAGES += library/desktop/cairo
REQUIRED_PACKAGES += library/desktop/gdk-pixbuf
REQUIRED_PACKAGES += library/desktop/gtk2
REQUIRED_PACKAGES += library/desktop/pango
REQUIRED_PACKAGES += library/expat
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/libnotify
REQUIRED_PACKAGES += library/libsecret
REQUIRED_PACKAGES += library/pcre2
REQUIRED_PACKAGES += library/sdl2
REQUIRED_PACKAGES += library/zlib
REQUIRED_PACKAGES += shell/ksh93
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/fontconfig
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += web/curl
REQUIRED_PACKAGES += x11/library/libsm
REQUIRED_PACKAGES += x11/library/libx11
REQUIRED_PACKAGES += x11/library/libxkbcommon
REQUIRED_PACKAGES += x11/library/libxtst
REQUIRED_PACKAGES += x11/library/libxxf86vm
