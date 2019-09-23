#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-messaging
PKG_VERSION:=0.5.12
PKG_RELEASE:=2

PKG_LICENSE:=GPL
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/pmarti/python-messaging.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

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

define Package/python-messaging/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/pmarti/python-messaging
	MAINTAINER:=Emmanuel Kala <emmanuel@brck.com>
	DEPENDS:=+python
endef


define Package/python-messaging
	$(call Package/python-messaging/Default)
	TITLE:=python-messaging
	VARIANT:=python
endef

define Package/python3-messaging
	$(call Package/python-messaging/Default)
	TITLE:=python3-messaging
	VARIANT:=python3
endef

define Package/python-messaging/description
	Pure Python SMS/MMS encoder/decoder
endef

define Package/python3-messaging/description
	$(call Package/python-messaging/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-messaging))
$(eval $(call BuildPackage,python-messaging))
$(eval $(call Py3Package,python3-messaging))
$(eval $(call BuildPackage,python3-messaging))
