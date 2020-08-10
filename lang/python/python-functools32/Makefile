include $(TOPDIR)/rules.mk

PKG_NAME:=python-functools32
PKG_VERSION:=3.2.3-2
PKG_RELEASE:=3

PKG_SOURCE:=functools32-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/5e/1a/0aa2c8195a204a9f51284018562dea77e25511f02fe924fac202fc012172
PKG_HASH:=89d824aa6c358c421a234d7f9ee0bd75933a67c29588ce50aaa3acdf4d403fa0

PKG_BUILD_DIR:=$(BUILD_DIR)/functools32-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk

define Package/python-functools32/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python functools32
	URL:=https://github.com/MiCHiLU/python-functools32
endef

define Package/python-functools32
$(call Package/python-functools32/Default)
  DEPENDS:=+PACKAGE_python-functools32:python-light
  VARIANT:=python
endef

define Package/python-functools32/description
  Backport of the functools module from Python 3.2.3 for use on 2.7 and PyPy.
endef

$(eval $(call PyPackage,python-functools32))
$(eval $(call BuildPackage,python-functools32))
$(eval $(call BuildPackage,python-functools32-src))
