#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-script
PKG_VERSION:=2.0.6
PKG_RELEASE:=1

PKG_SOURCE:=Flask-Script-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/00/a4/cd587b2b19f043b65bf33ceda2f6e4e6cdbd0ce18d01a52b9559781b1da6
PKG_HASH:=6425963d91054cfcc185807141c7314a9c5ad46325911bd24dcb489bd0161c65

PKG_BUILD_DIR:=$(BUILD_DIR)/flask-script-$(PKG_VERSION)
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

define Package/python-flask-script/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/corydolphin/flask-script
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-flask +python-six
endef


define Package/python-flask-script
	$(call Package/python-flask-script/Default)
	TITLE:=python-flask-script
	VARIANT:=python
endef

define Package/python3-flask-script
	$(call Package/python-flask-script/Default)
	TITLE:=python3-flask-script
	VARIANT:=python3
endef

define Package/python-flask-script/description
	Flask support for writing external scripts.
endef

define Package/python3-flask-script/description
	$(call Package/python-flask-script/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-flask-script))
$(eval $(call BuildPackage,python-flask-script))
$(eval $(call Py3Package,python3-flask-script))
$(eval $(call BuildPackage,python3-flask-script))
