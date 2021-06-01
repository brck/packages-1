#
# Copyright (C) 2019-2020 CZ.NIC, z. s. p. o. (https://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-sqlalchemy
PKG_VERSION:=1.3.13
PKG_RELEASE:=1

PYPI_NAME:=SQLAlchemy
PKG_HASH:=64a7b71846db6423807e96820993fa12a03b89127d278290ca25c0b11ed7b4fb

PKG_MAINTAINER:=Josef Schlehofer <josef.schlehofer@nic.cz>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_CPE_ID:=cpe:/a:sqlalchemy:sqlalchemy

include ../pypi.mk

OW_VER:=$(shell git --git-dir=$(TOPDIR)/.git describe --abbrev=0 --always --tag)
ifneq ($(filter reboot v19.07% v18.06%, $(OW_VER)),)
        IS_HEAD:=y
endif

include $(INCLUDE_DIR)/package.mk

ifeq ($(IS_HEAD),y)
        include ../python-package.mk
        include ../python3-package.mk
else
        $(call include_mk, python-package.mk)
        $(call include_mk, python3-package.mk)
endif

define Package/python-sqlalchemy/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://www.sqlalchemy.org
endef

define Package/python-sqlalchemy
        $(call Package/python-sqlalchemy/Default)
        TITLE:=python-sqlalchemy
        DEPENDS:= \
                +python-light \
                +python-urllib3 \
                +python-decimal \
                +python-logging
        VARIANT:=python
endef

define Package/python3-sqlalchemy
	$(call Package/python-sqlalchemy/Default)
  	TITLE:=python3-sqlalchemy
  	DEPENDS:= \
		+python3-light \
		+python3-urllib3 \
		+python3-decimal \
		+python3-logging
  	VARIANT:=python3
endef

define Package/python-sqlalchemy/description
  SQLAlchemy is the Python SQL toolkit and Object Relational Mapper
  that gives application developers the full power and flexibility of SQL.
  SQLAlchemy provides a full suite of well known enterprise-level persistence patterns,
  designed for efficient and high-performing database access,
  adapted into a simple and Pythonic domain language.
endef

define Package/python3-sqlalchemy/description
	$(call Package/python-sqlalchemy/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-sqlalchemy))
$(eval $(call BuildPackage,python-sqlalchemy))
$(eval $(call Py3Package,python3-sqlalchemy))
$(eval $(call BuildPackage,python3-sqlalchemy))
