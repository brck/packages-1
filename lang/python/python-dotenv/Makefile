#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-dotenv
PKG_VERSION:=0.10.3
PKG_RELEASE:=1

PKG_SOURCE:=python-dotenv-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/29/72/c3f4a251fd2dfcacddfb2e15e069e8345c0cde38ac0a6da8be5081de35d2
PKG_HASH:=f157d71d5fec9d4bd5f51c82746b6344dffa680ee85217c123f4a0c8117c4544

PKG_BUILD_DIR:=$(BUILD_DIR)/python-dotenv-$(PKG_VERSION)
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

define Package/python-dotenv/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://github.com/theskumar/python-dotenv
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-dotenv
	$(call Package/python-dotenv/Default)
	TITLE:=python-dotenv
	VARIANT:=python
        DEPENDS:=+python +python-typing
endef

define Package/python3-dotenv
	$(call Package/python-dotenv/Default)
	TITLE:=python3-dotenv
	VARIANT:=python3
        DEPENDS:=+python3 +python3-typing
endef

define Package/python-dotenv/description
	Add .env support to your django/flask apps in development and deployments
endef

define Package/python3-dotenv/description
	$(call Package/python-dotenv/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-dotenv))
$(eval $(call BuildPackage,python-dotenv))
$(eval $(call Py3Package,python3-dotenv))
$(eval $(call BuildPackage,python3-dotenv))
