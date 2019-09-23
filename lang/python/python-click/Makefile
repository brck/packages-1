#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#


include $(TOPDIR)/rules.mk

include $(TOPDIR)/rules.mk

PKG_NAME:=python-click
PKG_VERSION:=6.7
PKG_RELEASE:=2

PKG_SOURCE:=click-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/95/d9/c3336b6b5711c3ab9d1d3a80f1a3e2afeb9d8c02a7166462f6cc96570897
PKG_SHA256SUM:=f15516df478d5a56180fbf80e68f206010e6d160fc39fa508b65e035fd75130b

PKG_BUILD_DIR:=$(BUILD_DIR)/click-$(PKG_VERSION)
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

define Package/python-click/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://click.sqlalchemy.org/
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-mako +python-dateutil +python-editor +python-sqlalchemy
endef


define Package/python-click
	$(call Package/python-click/Default)
	TITLE:=python-click
	VARIANT:=python
endef

define Package/python3-click
	TITLE:=python3-click
	VARIANT:=python3
endef

define Package/python-click/description
	A simple wrapper around optparse for powerful command line utilities.
endef

define Package/python3-click/description
	A simple wrapper around optparse for powerful command line utilities.
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-click))
$(eval $(call BuildPackage,python-click))
$(eval $(call Py3Package,python3-click))
$(eval $(call BuildPackage,python3-click))
