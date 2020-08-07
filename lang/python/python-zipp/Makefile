include $(TOPDIR)/rules.mk

PKG_NAME:=python-zipp
PKG_VERSION:=1.2.0
PKG_RELEASE:=1

PYPI_NAME:=zipp
PKG_HASH:=c70410551488251b0fee67b460fb9a536af8d6f9f008ad10ac51f615b6a521b1

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-zipp/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python zipp
	URL:=https://github.com/jaraco/zipp
endef

define Package/python-zipp
$(call Package/python-zipp/Default)
  DEPENDS:=+PACKAGE_python-zipp:python-light
  VARIANT:=python
endef

define Package/python3-zipp
$(call Package/python-zipp/Default)
  DEPENDS:=+PACKAGE_python3-zipp:python3-light
  VARIANT:=python3
endef

define Package/python-zipp/description
  Backport of pathlib-compatible object wrapper for zip files
endef

define Package/python3-zipp/description
$(call Package/python-zipp/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-zipp))
$(eval $(call BuildPackage,python-zipp))
$(eval $(call BuildPackage,python-zipp-src))

$(eval $(call Py3Package,python3-zipp))
$(eval $(call BuildPackage,python3-zipp))
$(eval $(call BuildPackage,python3-zipp-src))
