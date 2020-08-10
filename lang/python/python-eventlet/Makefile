include $(TOPDIR)/rules.mk

PKG_NAME:=python-eventlet
PKG_VERSION:=0.26.1
PKG_RELEASE:=2

PYPI_NAME:=eventlet
PKG_HASH:=4f4a43366b4cbd4a3f2f231816e5c3dae8ab316df9b7da11f0525e2800559f33

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-eventlet/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=eventlet
  URL:=http://eventlet.net/
endef

define Package/python-eventlet
$(call Package/python-eventlet/Default)
	DEPENDS:=+python-light +python-greenlet +python-monotonic +python-enum34 \
		+python-six +python-dnspython
  VARIANT:=python
endef

define Package/python3-eventlet
$(call Package/python-eventlet/Default)
  DEPENDS:=+python3-light +python3-greenlet +python3-monotonic \
		+python3-six +python3-dnspython
  VARIANT:=python3
endef

define Package/python-eventlet/description
  Highly concurrent networking library
endef

define Package/python3-eventlet/description
$(call Package/python-eventlet/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-eventlet))
$(eval $(call BuildPackage,python-eventlet))
$(eval $(call BuildPackage,python-eventlet-src))

$(eval $(call Py3Package,python3-eventlet))
$(eval $(call BuildPackage,python3-eventlet))
$(eval $(call BuildPackage,python3-eventlet-src))
