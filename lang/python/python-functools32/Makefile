include $(TOPDIR)/rules.mk

PKG_NAME:=python-functools32
PKG_VERSION:=3.2.3-2
PKG_RELEASE:=1

PKG_SOURCE:=functools32-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/c5/60/6ac26ad05857c601308d8fb9e87fa36d0ebf889423f47c3502ef034365db
PKG_HASH:=f6253dfbe0538ad2e387bd8fdfd9293c925d63553f5813c4e587745416501e6d

PKG_BUILD_DIR:=$(BUILD_DIR)/functools32-$(PKG_VERSION)
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

define Package/python-functools32/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/MiCHiLU/python-functools32
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python
endef

define Package/python-functools32
  $(call Package/python-functools32/Default)
  TITLE:=python-functools32
  VARIANT:=python
endef

define Package/python-functools32/description
	Backport of the functools module from Python 3.2.3 for use on 2.7 and PyPy.
endef

$(eval $(call PyPackage,python-functools32))
$(eval $(call BuildPackage,python-functools32))
