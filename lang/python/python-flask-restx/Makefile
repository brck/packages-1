include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-restx
PKG_VERSION:=0.2.0
PKG_RELEASE:=1

PKG_SOURCE:=flask-restx-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/5f/6e/f71db883f6228e09e7e8c7bf5f1068c0a853db992bcaebd105005b70c959
PKG_HASH:=ca87a1808333f4ec5a50a5740b44e6cd3879a4b940d559df3996877ec4a2f2a5

PKG_BUILD_DIR:=$(BUILD_DIR)/flask-restx-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python python-setuptools

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

define Package/python-flask-restx/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/python-restx/flask-restx
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-flask +python-werkzeug +python-pytz
endef

define Package/python-flask-restx
  $(call Package/python-flask-restx/Default)
  TITLE:=python-flask-restx
  VARIANT:=python
endef

define Package/python-flask-restx/description
	Fully featured framework for fast, easy and documented API development with Flask
endef

$(eval $(call PyPackage,python-flask-restx))
$(eval $(call BuildPackage,python-flask-restx))
