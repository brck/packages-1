include $(TOPDIR)/rules.mk

PKG_NAME:=python-aniso8601
PKG_VERSION:=8.0.0
PKG_RELEASE:=1

PYPI_NAME:=aniso8601
PKG_HASH:=529dcb1f5f26ee0df6c0a1ee84b7b27197c3c50fc3a6321d66c544689237d072

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-aniso8601/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python aniso8601
	URL:=https://bitbucket.org/nielsenb/aniso8601/src/master/
endef

define Package/python-aniso8601
$(call Package/python-aniso8601/Default)
  DEPENDS:=+PACKAGE_python-aniso8601:python-light \
  +PACKAGE_python-aniso8601:python-dateutil
  VARIANT:=python
endef

define Package/python3-aniso8601
$(call Package/python-aniso8601/Default)
  DEPENDS:=+PACKAGE_python3-aniso8601:python3-light \
  +PACKAGE_python-aniso8601:python-dateutil
  VARIANT:=python3
endef

define Package/python-aniso8601/description
  Another ISO8601 parser for Python.
endef

define Package/python3-aniso8601/description
$(call Package/python-aniso8601/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-aniso8601))
$(eval $(call BuildPackage,python-aniso8601))
$(eval $(call BuildPackage,python-aniso8601-src))

$(eval $(call Py3Package,python3-aniso8601))
$(eval $(call BuildPackage,python3-aniso8601))
$(eval $(call BuildPackage,python3-aniso8601-src))
