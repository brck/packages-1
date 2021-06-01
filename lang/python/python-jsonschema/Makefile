include $(TOPDIR)/rules.mk

PKG_NAME:=python-jsonschema
PKG_VERSION:=3.2.0
PKG_RELEASE:=2

PYPI_NAME:=jsonschema
PKG_HASH:=c8a85b28d377cc7737e46e2d9f2b4f44ee3c0e1deac6bf46ddefc7187d30797a

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk

define Package/python-jsonschema/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python jsonschema
	URL:=https://github.com/Julian/jsonschema
endef

define Package/python-jsonschema
$(call Package/python-jsonschema/Default)
  DEPENDS:=+python-light +python-attrs +python-configparser +python-contextlib2 \
    +python-functools32 +python-pathlib2 +python-pyrsistent +python-scandir \
    +python-six +python-zipp +python-importlib-metadata
  VARIANT:=python
endef

define Package/python-jsonschema/description
  An implementation of JSON Schema validation for Python
endef

$(eval $(call PyPackage,python-jsonschema))
$(eval $(call BuildPackage,python-jsonschema))
$(eval $(call BuildPackage,python-jsonschema-src))
