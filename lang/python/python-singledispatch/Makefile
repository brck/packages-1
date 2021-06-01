include $(TOPDIR)/rules.mk

PKG_NAME:=python-singledispatch
PKG_VERSION:=3.4.0.3
PKG_RELEASE:=1

PYPI_NAME:=singledispatch
PKG_HASH:=5b06af87df13818d14f08a028e42f566640aef80805c3b50c5056b086e3c2b9c

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-singledispatch/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python singledispatch
	URL:=http://docs.python.org/3/library/functools.html#functools.singledispatch
endef

define Package/python-singledispatch
$(call Package/python-singledispatch/Default)
  DEPENDS:=+PACKAGE_python-singledispatch:python-light
  VARIANT:=python
endef

define Package/python3-singledispatch
$(call Package/python-singledispatch/Default)
  DEPENDS:=+PACKAGE_python3-singledispatch:python3-light
  VARIANT:=python3
endef

define Package/python-singledispatch/description
  This library brings functools.singledispatch from Python 3.4 to Python 2.6-3.3.
endef

define Package/python3-singledispatch/description
$(call Package/python-singledispatch/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-singledispatch))
$(eval $(call BuildPackage,python-singledispatch))
$(eval $(call BuildPackage,python-singledispatch-src))

$(eval $(call Py3Package,python3-singledispatch))
$(eval $(call BuildPackage,python3-singledispatch))
$(eval $(call BuildPackage,python3-singledispatch-src))
