# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask
PKG_VERSION:=0.11.1
PKG_RELEASE:=1

PKG_SOURCE:=Flask-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/55/8a/78e165d30f0c8bb5d57c429a30ee5749825ed461ad6c959688872643ffb3
PKG_MD5SUM:=d2af95d8fe79cf7da099f062dd122a08

PKG_BUILD_DIR:=$(BUILD_DIR)/Flask-$(PKG_VERSION)
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

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-flask/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/pallets/flask
	MAINTAINER:=Edoardo Biraghi <edoardo@brck.com>
endef

define Package/python-flask
	$(call Package/python-flask/Default)
	TITLE:=python-flask
	VARIANT:=python
	DEPENDS:=+python-click +python-codecs +python-decimal \
           +python-itsdangerous +python-jinja2 +python +python-logging \
           +python-markupsafe +python-multiprocessing +python-setuptools \
           +python-werkzeug
endef

define Package/python3-flask
	$(call Package/python-flask/Default)
	TITLE:=python3-flask
	VARIANT:=python3
	DEPENDS:=+PACKAGE_python3-flask:python3-asyncio +python3-click +python3-codecs +python3-decimal \
           +python3-itsdangerous +python3-jinja2 +python3 +python3-logging \
           +python3-markupsafe +python3-multiprocessing +python3-setuptools \
           +python3-werkzeug
endef

define Package/python-flask/description
	A microframework based on Werkzeug, Jinja2 and good intentions. 
endef

define Package/python3-flask/description
	A microframework based on Werkzeug, Jinja2 and good intentions.
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-flask))
$(eval $(call BuildPackage,python-flask))
$(eval $(call Py3Package,python3-flask))
$(eval $(call BuildPackage,python3-flask))
