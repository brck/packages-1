#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-caching
PKG_VERSION:=1.7.2
PKG_RELEASE:=1

PKG_SOURCE:=Flask-Caching-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/e8/85/8ccb4ed2aca8490927b4aa00b877f72fb9b3b687c04d2922c93a632fc911
PKG_HASH:=52e236cbc836c41a5ced0c0a67b48ad180c9e2b5cb69e881089bba766db5569e

PKG_BUILD_DIR:=$(BUILD_DIR)/flask-caching-$(PKG_VERSION)
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

define Package/python-flask-caching/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/sh4nks/flask-caching
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-flask
endef


define Package/python-flask-caching
	$(call Package/python-flask-caching/Default)
	TITLE:=python-flask-caching
	VARIANT:=python
endef

define Package/python3-flask-caching
	$(call Package/python-flask-caching/Default)
	TITLE:=python3-flask-caching
	VARIANT:=python3
endef

define Package/python-flask-caching/description
	Adds easy cache support to Flask.
endef

define Package/python3-flask-caching/description
	$(call Package/python-flask-caching/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-flask-caching))
$(eval $(call BuildPackage,python-flask-caching))
$(eval $(call Py3Package,python3-flask-caching))
$(eval $(call BuildPackage,python3-flask-caching))
