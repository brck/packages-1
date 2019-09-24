#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-pySMART
PKG_VERSION:=0.3
PKG_RELEASE:=1

PKG_SOURCE:=pySMART-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/ea/68/bdfdd6cbe8368d493faa7351f3aad5ee7e2792480090738804ca54352ea6
PKG_HASH:=d4a13d4facc23d8878358994cd355398836a616acc78e285a40d626cecd0817f

PKG_BUILD_DIR:=$(BUILD_DIR)/pySMART-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

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

define Package/python-pySMART/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://pypi.org/project/pySMART
	MAINTAINER:=Wambui Karuga <wambui@brck.com>
endef

define Package/python-pySMART
	$(call Package/python-pySMART/Default)
	TITLE:=python-pySMART
	VARIANT:=python
	DEPENDS:=+python
endef

define Package/python3-pySMART
	$(call Package/python-pySMART/Default)
	TITLE:=python3-pySMART
	VARIANT:=python3
	DEPENDS:=+python3
endef

define Package/python-pySMART/description
	A Python wrapper around smartmontools/smartctl. 
endef

define Package/python3-pySMART/description
	$(call Package/python-pySMART/description)
	Variant for Python 3.
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-pySMART/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-pySMART))
$(eval $(call Py3Package,python3-pySMART))
$(eval $(call BuildPackage,python3-pySMART))
