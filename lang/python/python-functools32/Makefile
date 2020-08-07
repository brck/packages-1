include $(TOPDIR)/rules.mk

PKG_NAME:=python-functools32
PKG_VERSION:=3.2.3-2
PKG_RELEASE:=1

PYPI_NAME:=functools32
PKG_HASH:=89d824aa6c358c421a234d7f9ee0bd75933a67c29588ce50aaa3acdf4d403fa0

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

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

define Package/python3-functools32
$(call Package/python-functools32/Default)
  DEPENDS:=+PACKAGE_python3-functools32:python3-light
  VARIANT:=python3
endef

define Package/python-functools32/description
  Backport of the functools module from Python 3.2.3 for use on 2.7 and PyPy.
endef

define Package/python3-functools32/description
$(call Package/python-functools32/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-functools32))
$(eval $(call BuildPackage,python-functools32))
$(eval $(call BuildPackage,python-functools32-src))

$(eval $(call Py3Package,python3-functools32))
$(eval $(call BuildPackage,python3-functools32))
$(eval $(call BuildPackage,python3-functools32-src))
