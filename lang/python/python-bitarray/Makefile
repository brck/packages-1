include $(TOPDIR)/rules.mk

PKG_NAME:=python-bitarray
PKG_VERSION:=0.9.3
PKG_RELEASE:=2

PKG_SOURCE:=bitarray-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/23/3e/ff197e545fd0f1d3796a4460a355c2beac92525823a3073cec66c03d63c3
PKG_HASH:=b2783d74247abb2669f581a001ecaa747e4b2ff9440762dbb499ed69b83e321e

PKG_BUILD_DIR:=$(BUILD_DIR)/bitarray-$(PKG_VERSION)
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

define Package/python-bitarray
	SECTION:=language-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=Python Bitarray
	URL:=https://github.com/ilanschnell/bitarray
	MAINTAINER:=Edoardo Biraghi <edoardo@brck.com>
	DEPENDS:=+python
endef

define Package/python-bitarray/description
	This module provides an object type which efficiently represents an array of booleans. 
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-bitarray/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-bitarray))
