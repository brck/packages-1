include $(TOPDIR)/rules.mk

PKG_NAME:=python-setuptools
PKG_VERSION:=44.1.1
PKG_RELEASE:=2

PKG_SOURCE:=setuptools-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/b2/40/4e00501c204b457f10fe410da0c97537214b2265247bc9a5bc6edd55b9e4
PKG_HASH:=c67aa55db532a0dadc4d2e20ba9961cbd3ccc84d544e9029699822542b5a476b

PKG_BUILD_DIR:=$(BUILD_DIR)/setuptools-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-setuptools/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python setuptools
	URL:=https://github.com/pypa/setuptools
endef

define Package/python-setuptools
$(call Package/python-setuptools/Default)
  DEPENDS:=+PACKAGE_python-setuptools:python-light
  VARIANT:=python
endef

define Package/python3-setuptools
$(call Package/python-setuptools/Default)
  DEPENDS:=+PACKAGE_python3-setuptools:python3-light
  VARIANT:=python3
endef

define Package/python-setuptools/description
  Easily download, build, install, upgrade, and uninstall Python packages
endef

define Package/python3-setuptools/description
$(call Package/python-setuptools/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-setuptools))
$(eval $(call BuildPackage,python-setuptools))
$(eval $(call BuildPackage,python-setuptools-src))

$(eval $(call Py3Package,python3-setuptools))
$(eval $(call BuildPackage,python3-setuptools))
$(eval $(call BuildPackage,python3-setuptools-src))
