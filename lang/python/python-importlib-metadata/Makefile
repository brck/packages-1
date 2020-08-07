include $(TOPDIR)/rules.mk

PKG_NAME:=python-importlib-metadata
PKG_VERSION:=1.7.0
PKG_RELEASE:=1

PYPI_NAME:=importlib-metadata
PKG_HASH:=90bb658cdbbf6d1735b6341ce708fc7024a3e14e99ffdc5783edea9f9b077f83

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-importlib-metadata/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python importlib-metadata
	URL:=http://importlib-metadata.readthedocs.io/
endef

define Package/python-importlib-metadata
$(call Package/python-importlib-metadata/Default)
  DEPENDS:=+PACKAGE_python-importlib-metadata:python-light \
  +PACKAGE_python-importlib-metadata:python-zipp
  VARIANT:=python
endef

define Package/python3-importlib-metadata
$(call Package/python-importlib-metadata/Default)
  DEPENDS:=+PACKAGE_python3-importlib-metadata:python3-light \
  +PACKAGE_python-importlib-metadata:python-zipp
  VARIANT:=python3
endef

define Package/python-importlib-metadata/description
  Read metadata from Python packages
endef

define Package/python3-importlib-metadata/description
$(call Package/python-importlib-metadata/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-importlib-metadata))
$(eval $(call BuildPackage,python-importlib-metadata))
$(eval $(call BuildPackage,python-importlib-metadata-src))

$(eval $(call Py3Package,python3-importlib-metadata))
$(eval $(call BuildPackage,python3-importlib-metadata))
$(eval $(call BuildPackage,python3-importlib-metadata-src))
