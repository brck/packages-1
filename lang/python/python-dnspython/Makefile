include $(TOPDIR)/rules.mk

PKG_NAME:=python-dnspython
PKG_VERSION:=1.16.0
PKG_RELEASE:=2

PKG_SOURCE:=dnspython-$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/ec/c5/14bcd63cb6d06092a004793399ec395405edf97c2301dfdc146dfbd5beed
PKG_HASH:=36c5e8e38d4369a08b6780b7f27d790a292b2b08eea01607865bf0936c558e01

PKG_BUILD_DIR:=$(BUILD_DIR)/dnspython-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-dnspython/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python dnspython
	URL:=https://www.dnspython.org/
endef

define Package/python-dnspython
$(call Package/python-dnspython/Default)
  DEPENDS:=+PACKAGE_python-dnspython:python-light
  VARIANT:=python
endef

define Package/python3-dnspython
$(call Package/python-dnspython/Default)
  DEPENDS:=+PACKAGE_python3-dnspython:python3-light
  VARIANT:=python3
endef

define Package/python-dnspython/description
	dnspython is a DNS toolkit for Python.
endef

define Package/python3-dnspython/description
$(call Package/python-dnspython/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-dnspython))
$(eval $(call BuildPackage,python-dnspython))
$(eval $(call Py3Package,python3-dnspython))
$(eval $(call BuildPackage,python3-dnspython))
