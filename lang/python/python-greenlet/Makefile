include $(TOPDIR)/rules.mk

PKG_NAME:=python-greenlet
PKG_VERSION:=0.4.7
PKG_RELEASE:=4

PKG_SOURCE:=greenlet-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/7a/9f/a1a0d9bdf3203ae1502c5a8434fe89d323599d78a106985bc327351a69d4
PKG_HASH:=f32c4fa4e06443e1bdb0d32b69e7617c25ff772c3ffc6d0aa63d192e9fd795fe

PKG_BUILD_DIR:=$(BUILD_DIR)/greenlet-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-greenlet/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python greenlet
  URL:=https://github.com/python-greenlet/greenlet
endef

define Package/python-greenlet
$(call Package/python-greenlet/Default)
  DEPENDS:=+PACKAGE_python-greenlet:python-light
  VARIANT:=python
endef

define Package/python3-greenlet
$(call Package/python-greenlet/Default)
  DEPENDS:=+PACKAGE_python3-greenlet:python3-light
  VARIANT:=python3
endef

define Package/python-greenlet/description
  Lightweight in-process concurrent programming
endef

define Package/python3-greenlet/description
$(call Package/python-greenlet/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-greenlet))
$(eval $(call BuildPackage,python-greenlet))
$(eval $(call BuildPackage,python-greenlet-src))

$(eval $(call Py3Package,python3-greenlet))
$(eval $(call BuildPackage,python3-greenlet))
$(eval $(call BuildPackage,python3-greenlet-src))
