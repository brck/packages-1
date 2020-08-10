include $(TOPDIR)/rules.mk

PKG_NAME:=python-greenlet
PKG_VERSION:=0.4.15
PKG_RELEASE:=3

PYPI_NAME:=greenlet
PKG_HASH:=9416443e219356e3c31f1f918a91badf2e37acf297e2fa13d24d1cc2380f8fbc

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-greenlet/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python greenlet
  URL:=https://github.com/python-greenlet/greenlet
endef

define Package/python-greenlet
$(call Package/python-greenlet/Default)
  DEPENDS:=+PACKAGE_python-greenlet:python-light
  VARIANT:=python
endef

define Package/python3-greenlet
$(call Package/python-greenlet/Default)
  DEPENDS:=+PACKAGE_python3-greenlet:python3-light
  VARIANT:=python3
endef

define Package/python-greenlet/description
  Lightweight in-process concurrent programming
endef

define Package/python3-greenlet/description
$(call Package/python-greenlet/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-greenlet))
$(eval $(call BuildPackage,python-greenlet))
$(eval $(call BuildPackage,python-greenlet-src))

$(eval $(call Py3Package,python3-greenlet))
$(eval $(call BuildPackage,python3-greenlet))
$(eval $(call BuildPackage,python3-greenlet-src))
