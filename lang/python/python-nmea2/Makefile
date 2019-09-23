#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-pynmea2
PKG_VERSION:=1.9.0
PKG_RELEASE:=2

PKG_SOURCE:=pynmea2-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/97/1b/891157b1c416cc597ab9bd7b47ae3347d31a8a8b16b50de35a710ae338d4
PKG_MD5SUM:=7c468ec59e9cdef0b04eed479a8fae8b

PKG_BUILD_DIR:=$(BUILD_DIR)/pynmea2-$(PKG_VERSION)

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

define Package/python-pynmea2/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/Knio/pynmea2
	MAINTAINER:=Emmanuel Kala <emmanuel@brck.com>
	DEPENDS:=+python
endef


define Package/python-pynmea2
	$(call Package/python-pynmea2/Default)
	TITLE:=python-pynmea2
	VARIANT:=python
endef

define Package/python3-pynmea2
	$(call Package/python-pynmea2/Default)
	TITLE:=python3-pynmea2
	VARIANT:=python3
endef

define Package/python-pynmea2/description
	Python library for parsing the NMEA 0183 protocol (GPS)
endef

define Package/python3-pynmea2/description
	$(call Package/python-pynmea2/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-pynmea2))
$(eval $(call BuildPackage,python-pynmea2))
$(eval $(call Py3Package,python3-pynmea2))
$(eval $(call BuildPackage,python3-pynmea2))
