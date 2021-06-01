include $(TOPDIR)/rules.mk

PKG_NAME:=python-greenlet
PKG_VERSION:=0.4.2
PKG_RELEASE:=7

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/python-greenlet/greenlet.git
PKG_SOURCE_VERSION:=4300791bbc9b4976fc54ded1d234849693bae462
PKG_SOURCE:=greenlet-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=greenlet-$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/greenlet-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

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
  DEPENDS:=+PACKAGE_python-greenlet:python
  VARIANT:=python
endef

define Package/python3-greenlet
$(call Package/python-greenlet/Default)
  DEPENDS:=+PACKAGE_python3-greenlet:python3
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

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix="$(PKG_INSTALL_DIR)/usr")
endef

define Package/python-greenlet/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)/usr/* \
	    $(1)/usr/
endef

$(eval $(call PyPackage,python-greenlet))
$(eval $(call BuildPackage,python-greenlet))
$(eval $(call BuildPackage,python-greenlet-src))

$(eval $(call Py3Package,python3-greenlet))
$(eval $(call BuildPackage,python3-greenlet))
$(eval $(call BuildPackage,python3-greenlet-src))
