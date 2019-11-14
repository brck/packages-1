#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-editor
PKG_VERSION:=1.0.4
PKG_RELEASE:=1

PKG_SOURCE:=python-editor-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/0a/85/78f4a216d28343a67b7397c99825cff336330893f00601443f7c7b2f2234
PKG_HASH:=51fda6bcc5ddbbb7063b2af7509e43bd84bfc32a4ff71349ec7847713882327b

PKG_BUILD_DIR:=$(BUILD_DIR)/python-editor-$(PKG_VERSION)
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

define Package/python-editor/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/fmoo/python-editor
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-editor
	$(call Package/python-editor/Default)
	TITLE:=python-editor
	VARIANT:=python
	DEPENDS:=+python
endef

define Package/python3-editor
	$(call Package/python-editor/Default)
	TITLE:=python3-editor
	VARIANT:=python3
	DEPENDS:=+python3
endef

define Package/python-editor/description
	python-editor is a library that provides the editor 
	module for programmatically interfacing with your system’s $$EDITOR.
endef

define Package/python3-editor/description
	$(call Package/python-editor/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-editor))
$(eval $(call BuildPackage,python-editor))
$(eval $(call Py3Package,python3-editor))
$(eval $(call BuildPackage,python3-editor))
