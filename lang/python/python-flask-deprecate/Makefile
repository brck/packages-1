include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-deprecate
PKG_VERSION:=0.1.3
PKG_RELEASE:=2

PYPI_NAME:=flask-deprecate
PKG_HASH:=4c184765622e6d9baadab929ac54bc818d43ee074c94649efd623ec0e7875274

PKG_MAINTAINER:=BRCK <dev@brck.com>
PKG_LICENSE:=MIT

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-flask-deprecate/Default
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python-flask-deprecate
  URL:=https://github.com/timmartin19/flask-deprecate
endef

define Package/python-flask-deprecate
$(call Package/python-flask-deprecate/Default)
  DEPENDS:=+PACKAGE_python-flask-deprecate:python +PACKAGE_python-flask-deprecate:python-flask 
  VARIANT:=python
endef

define Package/python3-flask-deprecate
$(call Package/python-flask-deprecate/Default)
  DEPENDS:=+PACKAGE_python3-flask-deprecate:python3 +PACKAGE_python3-flask-deprecate:python3-flask
  VARIANT:=python3
endef

define Package/python-flask-deprecate/description
  Easy decorators for deprecating flask views and blueprints.
endef

define Package/python3-flask-deprecate/description
$(call Package/python-flask-deprecate/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-flask-deprecate))
$(eval $(call BuildPackage,python-flask-deprecate))

$(eval $(call Py3Package,python3-flask-deprecate))
$(eval $(call BuildPackage,python3-flask-deprecate))
