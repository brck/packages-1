include $(TOPDIR)/rules.mk

PKG_NAME:=python-pathlib2
PKG_VERSION:=2.3.5
PKG_RELEASE:=1

PYPI_NAME:=pathlib2
PKG_HASH:=6cd9a47b597b37cc57de1c05e56fb1a1c9cc9fab04fe78c29acd090418529868

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-pathlib2/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python pathlib2
	URL:=https://github.com/mcmtroffaes/pathlib2
endef

define Package/python-pathlib2
$(call Package/python-pathlib2/Default)
  DEPENDS:=+PACKAGE_python-pathlib2:python-light
  VARIANT:=python
endef

define Package/python3-pathlib2
$(call Package/python-pathlib2/Default)
  DEPENDS:=+PACKAGE_python3-pathlib2:python3-light
  VARIANT:=python3
endef

define Package/python-pathlib2/description
  Object-oriented filesystem paths
endef

define Package/python3-pathlib2/description
$(call Package/python-pathlib2/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-pathlib2))
$(eval $(call BuildPackage,python-pathlib2))
$(eval $(call BuildPackage,python-pathlib2-src))

$(eval $(call Py3Package,python3-pathlib2))
$(eval $(call BuildPackage,python3-pathlib2))
$(eval $(call BuildPackage,python3-pathlib2-src))
