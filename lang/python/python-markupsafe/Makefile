#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

PKG_NAME:=python-markupsafe
PKG_VERSION:=1.1.1
PKG_RELEASE:=1

PKG_SOURCE:=MarkupSafe-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/b9/2e/64db92e53b86efccfaea71321f597fa2e1b2bd3853d8ce658568f7a13094
PKG_HASH:=29872e92839765e546828bb7754a68c418d927cd064fd4708fab9fe9c8bb116b

PKG_BUILD_DIR:=$(BUILD_DIR)/MarkupSafe-$(PKG_VERSION)
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

define Package/python-markupsafe/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://palletsprojects.com/p/markupsafe/
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python
endef


define Package/python-markupsafe
	$(call Package/python-markupsafe/Default)
	TITLE:=python-markupsafe
	VARIANT:=python
endef

define Package/python3-markupsafe
	$(call Package/python-markupsafe/Default)
	TITLE:=python3-markupsafe
	VARIANT:=python3
endef

define Package/python-markupsafe/description
	MarkupSafe implements a text object that escapes characters
	so it is safe to use in HTML and XML. Characters that have
	special meanings are replaced so that they display as the actual characters.
	This mitigates injection attacks, meaning untrusted user
	input can safely be displayed on a page.
endef

define Package/python3-markupsafe/description
	$(call Package/python-markupsafe/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-markupsafe))
$(eval $(call BuildPackage,python-markupsafe))
$(eval $(call Py3Package,python3-markupsafe))
$(eval $(call BuildPackage,python3-markupsafe))
