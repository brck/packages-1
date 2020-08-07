include $(TOPDIR)/rules.mk

PKG_NAME:=python-contextlib2
PKG_VERSION:=0.6.0.post1
PKG_RELEASE:=1

PYPI_NAME:=contextlib2
PKG_HASH:=01f490098c18b19d2bd5bb5dc445b2054d2fa97f09a4280ba2c5f3c394c8162e

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-contextlib2/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python contextlib2
	URL:=https://contextlib2.readthedocs.io/en/stable/
endef

define Package/python-contextlib2
$(call Package/python-contextlib2/Default)
  DEPENDS:=+PACKAGE_python-contextlib2:python-light
  VARIANT:=python
endef

define Package/python3-contextlib2
$(call Package/python-contextlib2/Default)
  DEPENDS:=+PACKAGE_python3-contextlib2:python3-light
  VARIANT:=python3
endef

define Package/python-contextlib2/description
  Backports and enhancements for the contextlib module
endef

define Package/python3-contextlib2/description
$(call Package/python-contextlib2/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-contextlib2))
$(eval $(call BuildPackage,python-contextlib2))
$(eval $(call BuildPackage,python-contextlib2-src))

$(eval $(call Py3Package,python3-contextlib2))
$(eval $(call BuildPackage,python3-contextlib2))
$(eval $(call BuildPackage,python3-contextlib2-src))
