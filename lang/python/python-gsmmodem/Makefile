#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-gsmmodem
PKG_VERSION:=0.9
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/python-gsmmodem/
PKG_MD5SUM:=1708832d3655451f6e8d8bd86621a2e3

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

define Package/python-gsmmodem/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/faucamp/python-gsmmodem
	MAINTAINER:=Emmanuel Kala <emmanuel@brck.com>
	DEPENDS:=+python-pyserial
endef


define Package/python-gsmmodem
	$(call Package/python-gsmmodem/Default)
	TITLE:=python-gsmmodem
	VARIANT:=python
endef

define Package/python3-gsmmodem
	$(call Package/python-gsmmodem/Default)
	TITLE:=python3-gsmmodem
	VARIANT:=python3
endef

define Package/python-gsmmodem/description
	python-gsmmodem is a module that allows easy control of a GSM modem attached to
	the system. It also includes a couple of useful commandline utilities for interacting
	with a GSM modem.
endef

define Package/python3-gsmmodem/description
	$(call Package/python-gsmmodem/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-gsmmodem))
$(eval $(call BuildPackage,python-gsmmodem))
$(eval $(call Py3Package,python3-gsmmodem))
$(eval $(call BuildPackage,python3-gsmmodem))
