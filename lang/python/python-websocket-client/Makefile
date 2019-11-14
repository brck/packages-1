#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-websocket-client
PKG_VERSION:=0.56.0
PKG_RELEASE:=1

PKG_SOURCE:=websocket_client-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/c5/01/8c9c7de6c46f88e70b5a3276c791a2be82ae83d8e0d0cc030525ee2866fd
PKG_HASH:=1fd5520878b68b84b5748bb30e592b10d0a91529d5383f74f4964e72b297fd3a

PKG_BUILD_DIR:=$(BUILD_DIR)/websocket_client-$(PKG_VERSION)
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

define Package/python-websocket-client/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://github.com/theskumar/python-websocket-client
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-websocket-client
	$(call Package/python-websocket-client/Default)
	TITLE:=python-websocket-client
	VARIANT:=python
        DEPENDS:=+python +python-six
endef

define Package/python3-websocket-client
	$(call Package/python-websocket-client/Default)
	TITLE:=python3-websocket-client
	VARIANT:=python3
        DEPENDS:=+python3 +python3-six
endef

define Package/python-websocket-client/description
	websocket-client module is WebSocket client for python.
	This provide the low level APIs for WebSocket. All APIs are the synchronous functions.
endef

define Package/python3-websocket-client/description
	$(call Package/python-websocket-client/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-websocket-client))
$(eval $(call BuildPackage,python-websocket-client))
$(eval $(call Py3Package,python3-websocket-client))
$(eval $(call BuildPackage,python3-websocket-client))
