#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-sqlalchemy
PKG_VERSION:=2.4.0
PKG_RELEASE:=3

PKG_SOURCE:=Flask-SQLAlchemy-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/9b/62/80a56f9d223f0b89cdcf7d592455375f8c9d73866f337fa85f39f45fe0c5
PKG_HASH:=0c9609b0d72871c540a7945ea559c8fdf5455192d2db67219509aed680a3d45a

PKG_BUILD_DIR:=$(BUILD_DIR)/Flask-SQLAlchemy-$(PKG_VERSION)
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

define Package/python-flask-sqlalchemy/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/pallets/flask-sqlalchemy
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-flask +python-sqlalchemy
endef

define Package/python-flask-sqlalchemy
	$(call Package/python-flask-sqlalchemy/Default)
	TITLE:=Python Flask-SQLAlchemy
	VARIANT:=python
endef

define Package/python3-flask-sqlalchemy
	$(call Package/python-flask-sqlalchemy/Default)
	TITLE:=Python3 Flask-SQLAlchemy
	VARIANT:=python3
endef

define Package/python-flask-sqlalchemy/description
	Flask-SQLAlchemy is an extension for Flask that adds support for
	SQLAlchemy to your application. It aims to simplify using
	SQLAlchemy with Flask by providing useful defaults and
	extra helpers that make it easier to accomplish common tasks.
endef

define Package/python3-flask-sqlalchemy/description
	$(call Package/python-flask-sqlalchemy/description)
	.
	(Variant for Python3)
endef

$(eval $(call PyPackage,python-flask-sqlalchemy))
$(eval $(call BuildPackage,python-flask-sqlalchemy))
$(eval $(call Py3Package,python3-flask-sqlalchemy))
$(eval $(call BuildPackage,python3-flask-sqlalchemy))
