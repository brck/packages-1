#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-engineio
PKG_VERSION:=3.8.2
PKG_RELEASE:=1

PKG_SOURCE:=python-engineio-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/4a/fd/b0f237d285330f6ac8fbe1f3373058d0d2ce233c7d2956ecb017ee358bcd
PKG_HASH:=32f2458431c2492c8ab90d49ef60a7230b11da9ee5a3dcaa7f5a6d0302d22e33

PKG_BUILD_DIR:=$(BUILD_DIR)/python-engineio-$(PKG_VERSION)
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

define Package/python-engineio/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://github.com/miguelgrinberg/python-engineio/
	MAINTAINER:=BRCK <dev@brck.com>
endef

define Package/python-engineio
	$(call Package/python-engineio/Default)
	TITLE:=python-engineio
	VARIANT:=python
	DEPENDS:=+python +python-six
endef

define Package/python3-engineio
	$(call Package/python-engineio/Default)
	TITLE:=python3-engineio
	VARIANT:=python3
	DEPENDS:=+python3 +python3-six
endef

define Package/python-engineio/description
	Python implementation of the Engine.IO realtime client and server.
endef

define Package/python3-engineio/description
	$(call Package/python-engineio/description)
	Variant for Python 3.
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-engineio/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-engineio))
$(eval $(call Py3Package,python3-engineio))
$(eval $(call BuildPackage,python3-engineio))
