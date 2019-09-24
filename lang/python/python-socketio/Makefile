#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-socketio
PKG_VERSION:=4.2.0
PKG_RELEASE:=1

PKG_SOURCE:=python-socketio-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/08/82/72f144dcbd44f7442600d81e9d923ecf2e708e0b8d8caef7ccd445290d0b
PKG_HASH:=335bd0fab481d65edce4ab82c3bb5cac950afa843329ea7c38777cd56c8eba38

PKG_BUILD_DIR:=$(BUILD_DIR)/python-socketio-$(PKG_VERSION)
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

define Package/python-socketio/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://github.com/miguelgrinberg/python-socketio/
	MAINTAINER:=BRCK <dev@brck.com>
endef

define Package/python-socketio
	$(call Package/python-socketio/Default)
	TITLE:=python-socketio
	VARIANT:=python
	DEPENDS:=+python +python-engineio +python-six
endef

define Package/python3-socketio
	$(call Package/python-socketio/Default)
	TITLE:=python3-socketio
	VARIANT:=python3
	DEPENDS:=+python3 +python3-engineio +python3-six
endef

define Package/python-socketio/description
	Python implementation of the Socket.IO realtime client and server.
endef

define Package/python3-socketio/description
	$(call Package/python-socketio/description)
	Variant for Python 3.
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-socketio/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-socketio))
$(eval $(call Py3Package,python3-socketio))
$(eval $(call BuildPackage,python3-socketio))
