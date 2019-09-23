#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-cors
PKG_VERSION:=3.0.8
PKG_RELEASE:=1

PKG_SOURCE:=Flask-Cors-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/9e/11/ca8b95c5bf9644471601e425f0de8cbd09a506bb6c24842cb17a6cd1eea8
PKG_HASH:=72170423eb4612f0847318afff8c247b38bd516b7737adfc10d1c2cdbb382d16

PKG_BUILD_DIR:=$(BUILD_DIR)/Flask-Cors-$(PKG_VERSION)
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

define Package/python-flask-cors/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/corydolphin/flask-cors
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-flask +python-six
endef


define Package/python-flask-cors
	$(call Package/python-flask-cors/Default)
	TITLE:=python-flask-cors
	VARIANT:=python
endef

define Package/python3-flask-cors
	$(call Package/python-flask-cors/Default)
	TITLE:=python3-flask-cors
	VARIANT:=python3
endef

define Package/python-flask-cors/description
	A Flask extension for handling Cross Origin Resource Sharing (CORS), making cross-origin AJAX possible.
endef

define Package/python3-flask-cors/description
	$(call Package/python-flask-cors/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-flask-cors))
$(eval $(call BuildPackage,python-flask-cors))
$(eval $(call Py3Package,python3-flask-cors))
$(eval $(call BuildPackage,python3-flask-cors))
