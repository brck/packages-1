#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-wand
PKG_VERSION:=0.4.2
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/60/14/5bb6919170f796bcc0b3b42c41a8679394e397468f22e5d89159bcd39197/
PKG_MD5SUM:=6936a7e5f0a0fe43efce2a249dcd59dc

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
	DEPENDS:=+python
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

define Build/Compile
	$(call Build/Compile/PyMod,,\
		install --prefix=/usr --root=$(PKG_INSTALL_DIR) \
	)
endef

define Package/python-wand/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-wand))
$(eval $(call Py3Package,python3-wand))
$(eval $(call BuildPackage,python3-wand))
