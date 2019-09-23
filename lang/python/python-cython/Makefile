#
# Copyright (c) 2015 Quatanium Co., Ltd.
#
# Based on copyright (C) 2008-2010 openwrt
#
# This is free software, licensed under the GNU General Public License v2.
# License: http://www.gnu.org/licenses/gpl.html GPL version v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-cython
PKG_VERSION:=0.29.13
PKG_RELEASE:=1

PKG_SOURCE:=Cython-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/a5/1f/c7c5450c60a90ce058b47ecf60bb5be2bfe46f952ed1d3b95d1d677588be/
PKG_MD5SUM:=f8109a2a86cded40b3896ee7a63bc5a5
PKG_BUILD_DIR:=$(BUILD_DIR_HOST)/$(PKG_NAME)-$(PKG_VERSION)/

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

define Package/python-cython
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python-cython
  URL:=http://www.cython.org
  DEPENDS:=+python
endef

define Package/python-cython/description
  Cython is a language that should make writing C extensions for the Python language easier
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --no-cython-compile --prefix="$(PKG_INSTALL_DIR)/usr")
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)
endef

define Host/Compile/PyMod
	$(call HostPython, \
		cd $(HOST_BUILD_DIR)/$(strip $(1)); \
		CFLAGS="$(HOST_CFLAGS)" \
		CPPFLAGS="$(HOST_CPPFLAGS)" \
		LDFLAGS="$(HOST_LDFLAGS)" \
		$(3) \
		, \
		./setup.py $(2))
endef


define Host/Compile
	$(call Host/Compile/PyMod,, \
		install --no-cython-compile \
		--prefix="/usr" \
		--root="$(STAGING_DIR_HOST)")
endef

define Host/Install
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,python-cython))
