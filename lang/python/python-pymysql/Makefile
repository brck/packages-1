#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-pymysql
PKG_VERSION:=0.9.3
PKG_RELEASE:=1

PKG_SOURCE:=PyMySQL-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/da/15/23ba6592920e21cb40eb0fe0ea002d2b6177beb1ca8a4c1add5a8f32754d
PKG_HASH:=d8c059dcd81dedb85a9f034d5e22dcb4442c0b201908bede99e306d65ea7c8e7

PKG_BUILD_DIR:=$(BUILD_DIR)/PyMySQL-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

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

define Package/python-pymysql/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://github.com/theskumar/python-pymysql
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-pymysql
	$(call Package/python-pymysql/Default)
	TITLE:=python-pymysql
	VARIANT:=python
        DEPENDS:=+python
endef

define Package/python3-pymysql
	$(call Package/python-pymysql/Default)
	TITLE:=python3-pymysql
	VARIANT:=python3
        DEPENDS:=+python3
endef

define Package/python-pymysql/description
	This package contains a pure-Python MySQL client library, based on PEP 249.
endef

define Package/python3-pymysql/description
	$(call Package/python-pymysql/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-pymysql))
$(eval $(call BuildPackage,python-pymysql))
$(eval $(call Py3Package,python3-pymysql))
$(eval $(call BuildPackage,python3-pymysql))
