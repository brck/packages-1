include $(TOPDIR)/rules.mk

PKG_NAME:=python-scandir
PKG_VERSION:=1.10.0
PKG_RELEASE:=1

PYPI_NAME:=scandir
PKG_HASH:=4d4631f6062e658e9007ab3149a9b914f3548cb38bfb021c64f39a025ce578ae

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-scandir/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python scandir
	URL:=https://github.com/benhoyt/scandir
endef

define Package/python-scandir
$(call Package/python-scandir/Default)
  DEPENDS:=+PACKAGE_python-scandir:python-light
  VARIANT:=python
endef

define Package/python3-scandir
$(call Package/python-scandir/Default)
  DEPENDS:=+PACKAGE_python3-scandir:python3-light
  VARIANT:=python3
endef

define Package/python-scandir/description
  scandir, a better directory iterator and faster os.walk()
endef

define Package/python3-scandir/description
$(call Package/python-scandir/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-scandir))
$(eval $(call BuildPackage,python-scandir))
$(eval $(call BuildPackage,python-scandir-src))

$(eval $(call Py3Package,python3-scandir))
$(eval $(call BuildPackage,python3-scandir))
$(eval $(call BuildPackage,python3-scandir-src))
