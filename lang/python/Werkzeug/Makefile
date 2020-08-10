# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=Werkzeug
PKG_VERSION:=1.0.1
PKG_RELEASE:=2

PYPI_NAME:=$(PKG_NAME)
PKG_HASH:=6c80b1e5ad3665290ea39320b91e1be1e0d5f60652b964a3070216de83d2e47c

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE.rst
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-werkzeug/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Werkzeug
  URL:=https://palletsprojects.com/p/werkzeug/
endef

define Package/python-werkzeug
$(call Package/python-werkzeug/Default)
  DEPENDS:=+python-light +python-email
  VARIANT:=python
endef

define Package/python3-werkzeug
$(call Package/python-werkzeug/Default)
  DEPENDS:=+python3-light +python3-email
  VARIANT:=python3
endef

define Package/python-werkzeug/description
  Werkzeug is a comprehensive WSGI web application library.
endef

define Package/python3-werkzeug/description
$(call Package/python-werkzeug/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-werkzeug))
$(eval $(call BuildPackage,python-werkzeug))
$(eval $(call BuildPackage,python-werkzeug-src))

$(eval $(call Py3Package,python3-werkzeug))
$(eval $(call BuildPackage,python3-werkzeug))
$(eval $(call BuildPackage,python3-werkzeug-src))
