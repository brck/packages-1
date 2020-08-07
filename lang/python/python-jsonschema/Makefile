include $(TOPDIR)/rules.mk

PKG_NAME:=python-jsonschema
PKG_VERSION:=3.2.0
PKG_RELEASE:=1

PYPI_NAME:=jsonschema
PKG_HASH:=c8a85b28d377cc7737e46e2d9f2b4f44ee3c0e1deac6bf46ddefc7187d30797a

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-jsonschema/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python jsonschema
	URL:=https://github.com/Julian/jsonschema
endef

define Package/python-jsonschema
$(call Package/python-jsonschema/Default)
  DEPENDS:=+PACKAGE_python-jsonschema:python-light \
  +PACKAGE_python-jsonschema:python-attrs \
  +PACKAGE_python-jsonschema:python-configparser \
  +PACKAGE_python-jsonschema:python-contextlib2 \
  +PACKAGE_python-jsonschema:python-functools32 \
  +PACKAGE_python-jsonschema:python-pathlib2 \
  +PACKAGE_python-jsonschema:python-pyrsistent \
  +PACKAGE_python-jsonschema:python-scandir \
  +PACKAGE_python-jsonschema:python-six \
  +PACKAGE_python-jsonschema:python-zipp \
  +PACKAGE_python-jsonschema:python-importlib-metadata
  VARIANT:=python
endef

define Package/python3-jsonschema
$(call Package/python-jsonschema/Default)
  DEPENDS:=+PACKAGE_python3-jsonschema:python3-light \
  +PACKAGE_python-jsonschema:python-attrs \
  +PACKAGE_python-jsonschema:python-configparser \
  +PACKAGE_python-jsonschema:python-contextlib2 \
  +PACKAGE_python-jsonschema:python-functools32 \
  +PACKAGE_python-jsonschema:python-pathlib2 \
  +PACKAGE_python-jsonschema:python-pyrsistent \
  +PACKAGE_python-jsonschema:python-scandir \
  +PACKAGE_python-jsonschema:python-six \
  +PACKAGE_python-jsonschema:python-zipp \
  +PACKAGE_python-jsonschema:python-importlib-metadata
  VARIANT:=python3
endef

define Package/python-jsonschema/description
  An implementation of JSON Schema validation for Python
endef

define Package/python3-jsonschema/description
$(call Package/python-jsonschema/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-jsonschema))
$(eval $(call BuildPackage,python-jsonschema))
$(eval $(call BuildPackage,python-jsonschema-src))

$(eval $(call Py3Package,python3-jsonschema))
$(eval $(call BuildPackage,python3-jsonschema))
$(eval $(call BuildPackage,python3-jsonschema-src))
