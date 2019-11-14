#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-lorm
PKG_VERSION:=1.0.11
PKG_RELEASE:=2

PKG_SOURCE:=lorm-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/7e/9a/08c92a71492c815c0e522ec36732b05be9bea2cf880cedfc4312b99dc3c3
PKG_HASH:=f6af94c1a31225dbab4a724379cd5986462d7834acbf8c3a456f03f9c7fa4cd6

PKG_BUILD_DIR:=$(BUILD_DIR)/lorm-$(PKG_VERSION)
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

define Package/python-lorm/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://github.com/theskumar/python-lorm
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-lorm
	$(call Package/python-lorm/Default)
	TITLE:=python-lorm
	VARIANT:=python
        DEPENDS:=+python +python-pymysql
endef

define Package/python3-lorm
	$(call Package/python-lorm/Default)
	TITLE:=python3-lorm
	VARIANT:=python3
        DEPENDS:=+python3 +python3-pymysql
endef

define Package/python-lorm/description
	Lorm is a light weight mysql client library for Python.
	Built-in connection pool, Django style lookup expressions.
endef

define Package/python3-lorm/description
	$(call Package/python-lorm/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-lorm))
$(eval $(call BuildPackage,python-lorm))
$(eval $(call Py3Package,python3-lorm))
$(eval $(call BuildPackage,python3-lorm))
