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
# Copyright 2017 Gary Mills
# Copyright 2019 Michal Nowak
# Copyright 2022 Niklas Poslovski
#

USE_PARALLEL_BUILD= yes
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=         pidgin
COMPONENT_VERSION=      2.14.14
COMPONENT_SUMMARY=      Multiprotocol Instant Messaging Client
COMPONENT_PROJECT_URL=  https://www.pidgin.im
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH= sha256:0ffc9994def10260f98a55cd132deefa8dc4a9835451cc0e982747bd458e2356
COMPONENT_ARCHIVE_URL=  https://sourceforge.net/projects/$(COMPONENT_NAME)/files/Pidgin/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)/download
COMPONENT_FMRI=         communication/im/pidgin
COMPONENT_CLASSIFICATION=Applications/Internet
COMPONENT_LICENSE=      GPLv2
COMPONENT_LICENSE_FILE= COPYING

TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

PATH= $(PATH.gnu)

# We use libncurses and libpanel from /usr/gnu/lib/$(MACH64)
LDFLAGS += -L/usr/gnu/lib/$(MACH64) -R/usr/gnu/lib/$(MACH64)

COMPONENT_PREP_ACTION= ( cd $(@D) && \
	libtoolize --force && \
	intltoolize --force --copy --automake && \
	aclocal -I. && \
	automake -a -f -c && \
	autoconf )

COMPONENT_PRE_CONFIGURE_ACTION= ( cp -rp $(SOURCE_DIR)/* $(@D) && \
	cp -rp $(COMPONENT_DIR)/files/po-sun $(@D) && \
	cd $(@D)/po-sun && $(MAKE) )

CONFIGURE_SCRIPT=	$(@D)/configure

CONFIGURE_OPTIONS+=	--enable-gnutls=no
CONFIGURE_OPTIONS+=	--with-nss-includes=/usr/include/mps
CONFIGURE_OPTIONS+=	--with-nss-libs=/usr/lib/mps/64
CONFIGURE_OPTIONS+=	--with-nspr-includes=/usr/include/mps
CONFIGURE_OPTIONS+=	--with-nspr-libs=/usr/lib/mps/64
CONFIGURE_OPTIONS+=	--enable-gnome-keyring
CONFIGURE_OPTIONS+=	--disable-gevolution
CONFIGURE_OPTIONS+=	--enable-cap
CONFIGURE_OPTIONS+=	--disable-meanwhile
CONFIGURE_OPTIONS+=	--disable-nm
CONFIGURE_OPTIONS+=	--enable-consoleui
CONFIGURE_OPTIONS+=	--with-ncurses-headers=/usr/include/ncurses
CONFIGURE_OPTIONS+=	--disable-vv
CONFIGURE_OPTIONS+=	--enable-perl=yes
CONFIGURE_OPTIONS+=	--enable-cyrus-sasl=no

CONFIGURE_ENV+=	INTLTOOL_PERL=$(PERL)
CONFIGURE_ENV+=	PERL=$(PERL)
CONFIGURE_ENV+=	perlpath=$(PERL)
CONFIGURE_ENV+=	PYTHON=$(PYTHON)

CONFIGURE_ENV+=	CPPFLAGS="$(CPPFLAGS)"

# Auto-generated dependencies
PERL_REQUIRED_PACKAGES += runtime/perl
PYTHON_REQUIRED_PACKAGES += library/python/dbus-python
PYTHON_REQUIRED_PACKAGES += runtime/python
REQUIRED_PACKAGES += database/sqlite-3
REQUIRED_PACKAGES += gnome/accessibility/at-spi2-core
REQUIRED_PACKAGES += library/audio/gstreamer1
REQUIRED_PACKAGES += library/desktop/cairo
REQUIRED_PACKAGES += library/desktop/gdk-pixbuf
REQUIRED_PACKAGES += library/desktop/gtk2
REQUIRED_PACKAGES += library/desktop/gtkspell
REQUIRED_PACKAGES += library/desktop/pango
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/libgnt
REQUIRED_PACKAGES += library/libidn
REQUIRED_PACKAGES += library/libxml2
REQUIRED_PACKAGES += library/ncurses
REQUIRED_PACKAGES += library/nspr
REQUIRED_PACKAGES += runtime/tcl-8
REQUIRED_PACKAGES += runtime/tk-8
REQUIRED_PACKAGES += shell/ksh93
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/libdbus
REQUIRED_PACKAGES += system/library/libdbus-glib
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += system/library/mozilla-nss
REQUIRED_PACKAGES += system/network/avahi
REQUIRED_PACKAGES += x11/library/libice
REQUIRED_PACKAGES += x11/library/libsm
REQUIRED_PACKAGES += x11/library/libx11
REQUIRED_PACKAGES += x11/library/libxscrnsaver
