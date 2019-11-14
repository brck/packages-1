#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-websocket-server
PKG_VERSION:=0.4
PKG_RELEASE:=1

PKG_SOURCE:=websocket_server-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/74/64/e86581ee7775a2e08aca530b41e1a1e3ee6b320233b1eff301dcb86d1636
PKG_HASH:=91cd4b565d1e1b00ef107abcb2840a8090868b19543f3b38e1962d5f975d0c04

PKG_BUILD_DIR:=$(BUILD_DIR)/websocket_server-$(PKG_VERSION)
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

define Package/python-websocket-server/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://github.com/theskumar/python-websocket-server
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-websocket-server
	$(call Package/python-websocket-server/Default)
	TITLE:=python-websocket-server
	VARIANT:=python
        DEPENDS:=+python
endef

define Package/python3-websocket-server
	$(call Package/python-websocket-server/Default)
	TITLE:=python3-websocket-server
	VARIANT:=python3
        DEPENDS:=+python3
endef

define Package/python-websocket-server/description
	A minimalistic websocket server implementation
	with no dependencies that works both Python2 and Python3.
endef

define Package/python3-websocket-server/description
	$(call Package/python-websocket-server/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-websocket-server))
$(eval $(call BuildPackage,python-websocket-server))
$(eval $(call Py3Package,python3-websocket-server))
$(eval $(call BuildPackage,python3-websocket-server))
