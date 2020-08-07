include $(TOPDIR)/rules.mk

PKG_NAME:=python-dnspython
PKG_VERSION:=1.16.0
PKG_RELEASE:=1

PKG_SOURCE:=dnspython-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/ec/c5/14bcd63cb6d06092a004793399ec395405edf97c2301dfdc146dfbd5beed
PKG_HASH:=36c5e8e38d4369a08b6780b7f27d790a292b2b08eea01607865bf0936c558e01

PKG_BUILD_DIR:=$(BUILD_DIR)/dnspython-$(PKG_VERSION)
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

define Package/python-dnspython/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://www.dnspython.org/
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python
endef

define Package/python-dnspython
  $(call Package/python-dnspython/Default)
  TITLE:=python-dnspython
  VARIANT:=python
endef

define Package/python-dnspython/description
	dnspython is a DNS toolkit for Python.
endef

$(eval $(call PyPackage,python-dnspython))
$(eval $(call BuildPackage,python-dnspython))
