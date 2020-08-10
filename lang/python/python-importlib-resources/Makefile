include $(TOPDIR)/rules.mk

PKG_NAME:=python-importlib-resources
PKG_VERSION:=3.0.0
PKG_RELEASE:=2

PYPI_NAME:=importlib-resources
PYPI_SOURCE_NAME:=importlib_resources
PKG_HASH:=19f745a6eca188b490b1428c8d1d4a0d2368759f32370ea8fb89cad2ab1106c3

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-importlib-resources/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python importlib-resources
	URL:=https://importlib-resources.readthedocs.io/en/latest/
endef

define Package/python-importlib-resources
$(call Package/python-importlib-resources/Default)
  DEPENDS:=+PACKAGE_python-importlib-resources:python-light \
  +PACKAGE_python-importlib-resources:python-singledispatch \
  +PACKAGE_python-importlib-resources:python-six
  VARIANT:=python
endef

define Package/python3-importlib-resources
$(call Package/python-importlib-resources/Default)
  DEPENDS:=+PACKAGE_python3-importlib-resources:python3-light \
  +PACKAGE_python-importlib-resources:python-singledispatch \
  +PACKAGE_python-importlib-resources:python-six
  VARIANT:=python3
endef

define Package/python-importlib-resources/description
  Read resources from Python packages
endef

define Package/python3-importlib-resources/description
$(call Package/python-importlib-resources/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-importlib-resources))
$(eval $(call BuildPackage,python-importlib-resources))
$(eval $(call BuildPackage,python-importlib-resources-src))

$(eval $(call Py3Package,python3-importlib-resources))
$(eval $(call BuildPackage,python3-importlib-resources))
$(eval $(call BuildPackage,python3-importlib-resources-src))
