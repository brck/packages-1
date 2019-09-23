#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-migrate
PKG_VERSION:=2.5.2
PKG_RELEASE:=1

PKG_SOURCE:=Flask-Migrate-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/c5/36/906fd843dcd7996bca42ed5bf8e3d70bac64fd81fc492e099aa739c961db
PKG_HASH:=a96ff1875a49a40bd3e8ac04fce73fdb0870b9211e6168608cbafa4eb839d502

PKG_BUILD_DIR:=$(BUILD_DIR)/Flask-Migrate-$(PKG_VERSION)
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

define Package/python-flask-migrate/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-flask +python-alembic +python-flask-sqlalchemy
endef

define Package/python-flask-migrate
	$(call Package/python-flask-migrate/Default)
	TITLE:=Python Flask-Migrate
	VARIANT:=python
endef

define Package/python3-flask-migrate
	$(call Package/python-flask-migrate/Default)
	TITLE:=Python3 Flask-Migrate
	VARIANT:=python3
endef

define Package/python-flask-migrate/description
	SQLAlchemy database migrations for Flask applications using Alembic.
endef

define Package/python3-flask-migrate/description
	$(call Package/python-flask-migrate/description)
	.
	(Variant for Python3)
endef

$(eval $(call PyPackage,python-flask-migrate))
$(eval $(call BuildPackage,python-flask-migrate))
$(eval $(call Py3Package,python3-flask-migrate))
$(eval $(call BuildPackage,python3-flask-migrate))
