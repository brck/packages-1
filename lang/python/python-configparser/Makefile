include $(TOPDIR)/rules.mk

PKG_NAME:=python-configparser
PKG_VERSION:=4.0.2
PKG_RELEASE:=1

PKG_SOURCE:=configparser-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/16/4f/48975536bd488d3a272549eb795ac4a13a5f7fcdc8995def77fbef3532ee
PKG_HASH:=c7d282687a5308319bf3d2e7706e575c635b0a470342641c93bea0ea3b5331df

PKG_BUILD_DIR:=$(BUILD_DIR)/configparser-$(PKG_VERSION)
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

define Package/python-configparser/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/jaraco/configparser/
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python
endef

define Package/python-configparser
  $(call Package/python-configparser/Default)
  TITLE:=python-configparser
  VARIANT:=python
endef

define Package/python-configparser/description
	Updated configparser from Python 3.7 for Python 2.6+.
endef

$(eval $(call PyPackage,python-configparser))
$(eval $(call BuildPackage,python-configparser))
