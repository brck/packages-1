#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-mako
PKG_VERSION:=1.0.13
PKG_RELEASE:=1

PKG_SOURCE:=Mako-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/fa/29/8016763284d8fab844224f7cc5675cb4a388ebda0eb5a403260187e48435
PKG_HASH:=95ee720cc3453063788515d55bd7ce4a2a77b7b209e4ac70ec5c86091eb02541

PKG_BUILD_DIR:=$(BUILD_DIR)/Mako-$(PKG_VERSION)
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

define Package/python-mako/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://www.makotemplates.org/
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-markupsafe
endef


define Package/python-mako
	$(call Package/python-mako/Default)
	TITLE:=python-mako
	VARIANT:=python
endef

define Package/python3-mako
	$(call Package/python-mako/Default)
	TITLE:=python3-mako
	VARIANT:=python3
endef

define Package/python-mako/description
	Mako is a template library written in Python. It provides a familiar,
	non-XML syntax which compiles into Python modules for maximum performance.
	Mako’s syntax and API borrows from the best ideas of many others,
	including Django templates, Cheetah, Myghty, and Genshi.
	Conceptually, Mako is an embedded Python (i.e. Python Server Page) language,
	which refines the familiar ideas of componentized layout and inheritance
	to produce one of the most straightforward and flexible models available,
	while also maintaining close ties to Python calling and scoping semantics.
endef

define Package/python3-mako/description
	$(call Package/python-mako/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-mako))
$(eval $(call BuildPackage,python-mako))
$(eval $(call Py3Package,python3-mako))
$(eval $(call BuildPackage,python3-mako))
