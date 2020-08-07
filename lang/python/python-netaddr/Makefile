include $(TOPDIR)/rules.mk

PKG_NAME:=python-netaddr
PKG_VERSION:=0.8.0
PKG_RELEASE:=1

PYPI_NAME:=netaddr
PKG_HASH:=d6cc57c7a07b1d9d2e917aa8b36ae8ce61c35ba3fcd1b83ca31c5a0ee2b5a243

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-netaddr/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python netaddr
	URL:=https://github.com/netaddr/netaddr
endef

define Package/python-netaddr
$(call Package/python-netaddr/Default)
  DEPENDS:=+PACKAGE_python-netaddr:python-light \
  +PACKAGE_python-netaddr:python-contextlib2 \
  +PACKAGE_python-netaddr:python-pathlib2 \
  +PACKAGE_python-netaddr:python-scandir \
  +PACKAGE_python-netaddr:python-zipp \
  +PACKAGE_python-netaddr:python-singledispatch \
  +PACKAGE_python-netaddr:python-typing \
  +PACKAGE_python-netaddr:python-six \
  +PACKAGE_python-netaddr:python-importlib-resources
  VARIANT:=python
endef

define Package/python3-netaddr
$(call Package/python-netaddr/Default)
  DEPENDS:=+PACKAGE_python3-netaddr:python3-light \
  +PACKAGE_python-netaddr:python-contextlib2 \
  +PACKAGE_python-netaddr:python-pathlib2 \
  +PACKAGE_python-netaddr:python-scandir \
  +PACKAGE_python-netaddr:python-zipp \
  +PACKAGE_python-netaddr:python-singledispatch \
  +PACKAGE_python-netaddr:python-typing \
  +PACKAGE_python-netaddr:python-six \
  +PACKAGE_python-netaddr:python-importlib-resources
  VARIANT:=python3
endef

define Package/python-netaddr/description
  A network address manipulation library for Python
endef

define Package/python3-netaddr/description
$(call Package/python-netaddr/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-netaddr))
$(eval $(call BuildPackage,python-netaddr))
$(eval $(call BuildPackage,python-netaddr-src))

$(eval $(call Py3Package,python3-netaddr))
$(eval $(call BuildPackage,python3-netaddr))
$(eval $(call BuildPackage,python3-netaddr-src))
