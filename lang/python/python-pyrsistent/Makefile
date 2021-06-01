include $(TOPDIR)/rules.mk

PKG_NAME:=python-pyrsistent
PKG_VERSION:=0.15.7
PKG_RELEASE:=2

PYPI_NAME:=pyrsistent
PKG_HASH:=cdc7b5e3ed77bed61270a47d35434a30617b9becdf2478af76ad2c6ade307280

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-pyrsistent/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python pyrsistent
	URL:=http://github.com/tobgu/pyrsistent/
endef

define Package/python-pyrsistent
$(call Package/python-pyrsistent/Default)
  DEPENDS:=+PACKAGE_python-pyrsistent:python-light
  VARIANT:=python
endef

define Package/python3-pyrsistent
$(call Package/python-pyrsistent/Default)
  DEPENDS:=+PACKAGE_python3-pyrsistent:python3-light
  VARIANT:=python3
endef

define Package/python-pyrsistent/description
  Persistent/Functional/Immutable data structures
endef

define Package/python3-pyrsistent/description
$(call Package/python-pyrsistent/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-pyrsistent))
$(eval $(call BuildPackage,python-pyrsistent))
$(eval $(call BuildPackage,python-pyrsistent-src))

$(eval $(call Py3Package,python3-pyrsistent))
$(eval $(call BuildPackage,python3-pyrsistent))
$(eval $(call BuildPackage,python3-pyrsistent-src))
