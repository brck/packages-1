include $(TOPDIR)/rules.mk

PKG_NAME:=Flask
PKG_VERSION:=1.1.2
PKG_RELEASE:=2

PYPI_NAME:=$(PKG_NAME)
PKG_HASH:=4efa1ae2d7c9865af48986de8aeb8504bf32c7f3d6fdc9353d34b21f4b127060

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE.rst
PKG_MAINTAINER:=BRCK <dev@brck.com>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-flask/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Flask
  URL:=https://palletsprojects.com/p/flask/
endef

define Package/python-flask
$(call Package/python-flask/Default)
  DEPENDS:=+python-click +python-codecs +python-decimal \
           +python-itsdangerous +python-jinja2 +python +python-logging \
           +python-markupsafe +python-multiprocessing +python-setuptools \
           +python-werkzeug
  VARIANT:=python
endef

define Package/python3-flask
$(call Package/python-flask/Default)
  DEPENDS:=+python3-asyncio +python3-click +python3-codecs +python3-decimal \
          +python3-itsdangerous +python3-jinja2 +python3 +python3-logging \
          +python3-markupsafe +python3-multiprocessing +python3-setuptools \
          +python3-werkzeug
  VARIANT:=python3
endef

define Package/python-flask/description
  A simple framework for building complex web applications.
endef

define Package/python3-flask/description
$(call Package/python-flask/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-flask))
$(eval $(call BuildPackage,python-flask))
$(eval $(call BuildPackage,python-flask-src))

$(eval $(call Py3Package,python3-flask))
$(eval $(call BuildPackage,python3-flask))
$(eval $(call BuildPackage,python3-flask-src))
