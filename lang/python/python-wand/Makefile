#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-wand
PKG_VERSION:=0.4.5
PKG_RELEASE:=3
PKG_LICENSE:=GPL-2.0

PKG_SOURCE:=Wand-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/24/a1/018ac845f26168ba9a5d6a75259385625a449557965fb8a2f83eb33a1adb/
PKG_MD5SUM:=94b599e5762dd29c7c77d714f9e8c279

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

define Package/python-wand/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://pypi.python.org/pypi/Wand/
	MAINTAINER:=Emmanuel Kala <emmanuel@brck.com>
endef

define Package/python-wand
	$(call Package/python-wand/Default)
	TITLE:=python-wand
	VARIANT:=python
	DEPENDS:=+python +imagemagick
	PKG_BUILD_DEPENDS:=+libmagickwand/host
endef

define Package/python3-wand
	$(call Package/python-wand/Default)
	TITLE:=python3-wand
	VARIANT:=python3
	DEPENDS:=+python3
endef

define Package/python-wand/description
	Wand is a ctypes-based simple ImageMagick API binding for Python
endef

define Package/python3-wand/description
	$(call Package/python-wand/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-wand))
$(eval $(call BuildPackage,python-wand))
$(eval $(call Py3Package,python3-wand))
$(eval $(call BuildPackage,python3-wand))
