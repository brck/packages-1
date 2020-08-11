include $(TOPDIR)/rules.mk

PKG_NAME:=python-greenlet
PKG_VERSION:=0.4.2
PKG_RELEASE:=5

PKG_SOURCE:=greenlet-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/11/46/ce7c6f01fba12f86924f4e5b7730652322c8e6069d69f479ade516785c4f
PKG_HASH:=b160e556a22e16bae3f3f63ffce7898682c803cd896457192f7b54fe74fe991e

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
