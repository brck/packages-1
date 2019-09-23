#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-login
PKG_VERSION:=0.4.1
PKG_RELEASE:=2

PKG_SOURCE:=Flask-Login-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/c1/ff/bd9a4d2d81bf0c07d9e53e8cd3d675c56553719bbefd372df69bf1b3c1e4
PKG_HASH:=c815c1ac7b3e35e2081685e389a665f2c74d7e077cb93cecabaea352da4752ec

PKG_BUILD_DIR:=$(BUILD_DIR)/Flask-Login-$(PKG_VERSION)
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

define Package/python-flask-login/Default
	SECTION:=language-python
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/maxcountryman/flask-login
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-flask
endef

define Package/python-flask-login
	$(call Package/python-flask-login/Default)
	TITLE:=python-flask-login
	VARIANT:=python
endef

define Package/python3-flask-login
	$(call Package/python-flask-login/Default)
	TITLE:=python3-flask-login
	VARIANT:=python3
endef

define Package/python-flask-login/description
	Flask-Login provides user session management for Flask.
	It handles the common tasks of logging in, logging out,
	and remembering your users’ sessions over extended periods of time.
endef

define Package/python3-flask-login/description
	$(call Package/python-flask-login/description)
	.
	(Variant for Python3)
endef

$(eval $(call PyPackage,python-flask-login))
$(eval $(call BuildPackage,python-flask-login))
$(eval $(call Py3Package,python3-flask-login))
$(eval $(call BuildPackage,python3-flask-login))
