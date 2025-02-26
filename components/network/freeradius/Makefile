
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
# Copyright (c) 2024, Friedrich Kink
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		freeradius
COMPONENT_VERSION=	3.2.7
COMPONENT_VERSION_=	$(subst .,_,$(COMPONENT_VERSION))
COMPONENT_SUMMARY=	The FreeRADIUS server
COMPONENT_DESCRIPTION=	The FreeRADIUS Server Project is a high performance and highly \
		configurable multi-protocol policy server, supporting RADIUS, DHCPv4 DHCPv6, DNS, \
		TACACS+ and VMPS. Using RADIUS allows authentication and authorization for a \
		network to be centralized, and minimizes the number of changes that have to be \
		done when adding or deleting new users to a network.
COMPONENT_SRC=		$(COMPONENT_NAME)-server-release_$(COMPONENT_VERSION_)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_PROJECT_URL=	https://freeradius.org/
COMPONENT_ARCHIVE_URL=	https://github.com/FreeRADIUS/freeradius-server/archive/refs/tags/release_$(COMPONENT_VERSION_).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:ebb906a236a8db71ba96875c9e53405bc8493e363c3815af65ae829cb6c288a3
COMPONENT_FMRI=		network/radius
COMPONENT_CLASSIFICATION=	Applications/Internet
COMPONENT_LICENSE=	GPLv2
COMPONENT_LICENSE_FILE=	LICENSE

TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

COMPONENT_PRE_CONFIGURE_ACTION += ( \
	$(CLONEY) $(SOURCE_DIR) $(@D); \
	$(GSED) -i -e 's/-D_LIBRADIUS/-D_LIBRADIUS -D_XPG4_2/' $(@D)/src/lib/all.mk; );

CFLAGS += $(XPG6MODE)

CONFIGURE_OPTIONS += CFLAGS="-I/usr/include/odbc"
CONFIGURE_OPTIONS += LDFLAGS="-lldap_r"
CONFIGURE_OPTIONS += --srcdir=$(BUILD_DIR)/$(MACH64)
CONFIGURE_OPTIONS += --sysconfdir=$(ETCDIR)
CONFIGURE_OPTIONS += --localstatedir=$(VARDIR)
CONFIGURE_OPTIONS += --with-pcap-lib-dir=$(USRLIBDIR)
CONFIGURE_OPTIONS += --with-pcap-include-dir=/usr/include/pcap
CONFIGURE_OPTIONS += --with-rlm-ldap-include-dir=/usr/include/openldap
CONFIGURE_OPTIONS += --with-rlm-sql_postgresql-include-dir=/usr/postgres/$(PG_VERSION)/include
CONFIGURE_OPTIONS += --with-openssl-lib-dir=$(OPENSSL_LIBDIR)
CONFIGURE_OPTIONS += --with-openssl-include-dir=$(OPENSSL_INCDIR)
CONFIGURE_OPTIONS += --without-static-modules

COMPONENT_INSTALL_ARGS +=       R=$(PROTO_DIR)
COMPONENT_POST_INSTALL_ACTION =  \
	$(CP) $(SOURCE_DIR)/raddb/mods-config/attr_filter/* $(PROTOETCDIR)/raddb/mods-config/attr_filter ; \
	$(CP) $(SOURCE_DIR)/raddb/mods-config/files/* $(PROTOETCDIR)/raddb/mods-config/files ; \
	$(CP) $(SOURCE_DIR)/raddb/policy.d/* $(PROTOETCDIR)/raddb/policy.d ; \
	/usr/bin/elfedit -e 'dyn:value -s  RUNPATH "$(MYSQL_LIBDIR)"' $(PROTOUSRLIBDIR64)/rlm_sql_mysql.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  RPATH "$(MYSQL_LIBDIR)"' $(PROTOUSRLIBDIR64)/rlm_sql_mysql.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  RUNPATH "$(GCC_LIBDIR)"' $(PROTOUSRLIBDIR64)/rlm_sql_unixodbc.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  RPATH "$(GCC_LIBDIR)"' $(PROTOUSRLIBDIR64)/rlm_sql_unixodbc.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  RUNPATH "$(PG_LIBDIR)"' $(PROTOUSRLIBDIR64)/rlm_sql_postgresql.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  RPATH "$(PG_LIBDIR)"' $(PROTOUSRLIBDIR64)/rlm_sql_postgresql.so ; \
	/usr/bin/elfedit -e 'dyn:delete NEEDED' $(PROTOUSRLIBDIR64)/rlm_python.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  NEEDED "libpython$(PYTHON_VERSION).so.1.0"' $(PROTOUSRLIBDIR64)/rlm_python.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  RUNPATH "$(GCC_LIBDIR):$(USRLIBDIR)/python$(PYTHON_VERSION)/config-$(PYTHON_VERSION)"' $(PROTOUSRLIBDIR64)/rlm_python.so ; \
	/usr/bin/elfedit -e 'dyn:value -s  RPATH "$(GCC_LIBDIR):$(USRLIBDIR)/python$(PYTHON_VERSION)/config-$(PYTHON_VERSION)"' $(PROTOUSRLIBDIR64)/rlm_python.so ;

# Manually added build dependencies
REQUIRED_PACKAGES += $(PG_DEVELOPER_PKG)

# Auto-generated dependencies
PERL_REQUIRED_PACKAGES += runtime/perl
PYTHON_REQUIRED_PACKAGES += runtime/python
REQUIRED_PACKAGES += $(MYSQL_LIBRARY_PKG)
REQUIRED_PACKAGES += $(OPENSSL_PKG)
REQUIRED_PACKAGES += $(PG_LIBRARY_PKG)
REQUIRED_PACKAGES += $(READLINE_PKG)
REQUIRED_PACKAGES += SUNWcs
REQUIRED_PACKAGES += database/sqlite-3
REQUIRED_PACKAGES += library/database/gdbm
REQUIRED_PACKAGES += library/freetds
REQUIRED_PACKAGES += library/json-c
REQUIRED_PACKAGES += library/libmemcached
REQUIRED_PACKAGES += library/openldap
REQUIRED_PACKAGES += library/talloc
REQUIRED_PACKAGES += library/unixodbc
REQUIRED_PACKAGES += runtime/perl
REQUIRED_PACKAGES += service/network/unbound
REQUIRED_PACKAGES += service/security/kerberos-5
REQUIRED_PACKAGES += shell/ksh93
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/libpcap
REQUIRED_PACKAGES += web/curl
