#
# Copyright (C) 2007-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-gunicorn
PKG_VERSION:=19.2.0
PKG_RELEASE:=1

PKG_SOURCE:=gunicorn-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/g/gunicorn/
PKG_MD5SUM:=010e23e52324375ed9e2265d6e3be692

PKG_BUILD_DIR:=$(BUILD_DIR)/gunicorn-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/gunicorn/Default
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=WSGI HTTP Server for UNIX
  URL:=https://gunicorn.org
endef

define Package/python-gunicorn
$(call Package/gunicorn/Default)
  DEPENDS:=+python
  VARIANT:=python
endef

define Package/python-gunicorn/description
    WSGI HTTP Server for UNIX (libraries)
endef

define PyPackage/python-gunicorn/filespec
+|$(PYTHON_PKG_DIR)
-|$(PYTHON_PKG_DIR)/gunicorn/workers/_gaiohttp.py
endef

define Package/python3-gunicorn
$(call Package/gunicorn/Default)
  DEPENDS:=+python3
  VARIANT:=python3
endef

define Package/python3-gunicorn/description
$(call define Package/python-gunicorn/description)
.
(Variant for Python3)
endef

# Make sure that the binaries are not installed with the libraries
# That means adding some empty Py[3]Package/gunicorn[3]/install rules
define PyPackage/python-gunicorn/install
	:
endef

define Py3Package/python3-gunicorn/install
	:
endef

define Package/python-gunicorn
    SUBMENU:=Python
    SECTION:=lang
    CATEGORY:=Languages
    TITLE:=WSGI HTTP Server for UNIX
    URL:=https://gunicorn.org
    DEPENDS:=+python +python-setuptools
endef

define Package/python-gunicorn/description
    WSGI HTTP Server for UNIX
endef

define Package/gunicorn/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(call PyShebang,$(1)/usr/bin/*)
endef

define Package/python-gunicorn/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/gunicorn \
		$(1)/usr/bin/gunicorn3
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/gunicorn_paster \
		$(1)/usr/bin/gunicorn3_paster
	$(call Py3Shebang,$(1)/usr/bin/*)
endef

$(eval $(call PyPackage,python-gunicorn))
$(eval $(call BuildPackage,python-gunicorn))
