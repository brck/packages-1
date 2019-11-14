#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-typing
PKG_VERSION:=3.7.4
PKG_RELEASE:=1

PKG_SOURCE:=typing-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/60/e8/944bd083411be12c6d46d400a06744a5a85ad27d3c6e487a5da0d58950cc
PKG_HASH:=53765ec4f83a2b720214727e319607879fec4acde22c4fbb54fa2604e79e44ce

PKG_BUILD_DIR:=$(BUILD_DIR)/typing-$(PKG_VERSION)
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

define Package/python-typing/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://docs.python.org/3/library/typing.html
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-typing
	$(call Package/python-typing/Default)
	TITLE:=python-typing
	VARIANT:=python
endef

define Package/python3-typing
	$(call Package/python-typing/Default)
	TITLE:=python3-typing
	VARIANT:=python3
endef

define Package/python-typing/description
	Typing – Type Hints for Python.
endef

define Package/python3-typing/description
	$(call Package/python-typing/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-typing))
$(eval $(call BuildPackage,python-typing))
$(eval $(call Py3Package,python3-typing))
$(eval $(call BuildPackage,python3-typing))
