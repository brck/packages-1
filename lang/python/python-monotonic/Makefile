include $(TOPDIR)/rules.mk

PKG_NAME:=python-monotonic
PKG_VERSION:=1.5
PKG_RELEASE:=1

PYPI_NAME:=monotonic
PKG_HASH:=23953d55076df038541e648a53676fb24980f7a1be290cdda21300b3bc21dfb0

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-monotonic/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python monotonic
	URL:=https://github.com/atdt/monotonic
endef

define Package/python-monotonic
$(call Package/python-monotonic/Default)
  DEPENDS:=+PACKAGE_python-monotonic:python-light
  VARIANT:=python
endef

define Package/python3-monotonic
$(call Package/python-monotonic/Default)
  DEPENDS:=+PACKAGE_python3-monotonic:python3-light
  VARIANT:=python3
endef

define Package/python-monotonic/description
  An implementation of time.monotonic() for Python 2 & < 3.3
endef

define Package/python3-monotonic/description
$(call Package/python-monotonic/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-monotonic))
$(eval $(call BuildPackage,python-monotonic))
$(eval $(call BuildPackage,python-monotonic-src))

$(eval $(call Py3Package,python3-monotonic))
$(eval $(call BuildPackage,python3-monotonic))
$(eval $(call BuildPackage,python3-monotonic-src))
