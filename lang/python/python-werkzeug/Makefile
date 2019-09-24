# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-werkzeug
PKG_VERSION:=0.15.4
PKG_RELEASE:=1

PKG_SOURCE:=Werkzeug-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/59/2d/b24bab64b409e22f026fee6705b035cb0698399a7b69449c49442b30af47
PKG_HASH:=a0b915f0815982fb2a09161cb8f31708052d0951c3ba433ccc5e1aa276507ca6

PKG_BUILD_DIR:=$(BUILD_DIR)/Werkzeug-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

OW_VER:=$(shell git --git-dir=$(TOPDIR)/.git describe --abbrev=0 --always --tag)
ifneq ($(filter reboot v19.07% v18.06%, $(OW_VER)),)
        IS_HEAD:=y
endif

include $(INCLUDE_DIR)/package.mk

ifeq ($(IS_HEAD),y)
        include ../python-package.mk
        include ../python3-package.mk
else
        $(call include_mk, python-package.mk)
        $(call include_mk, python3-package.mk)
endif

define Package/python-werkzeug/Default
    SECTION:=lang
    CATEGORY:=Languages
    SUBMENU:=Python
    URL:=https://palletsprojects.com/p/werkzeug/
endef

define Package/python-werkzeug
    $(call Package/python-werkzeug/Default)
    TITLE:=python-werkzeug
    DEPENDS:=+python-light +python-email
    VARIANT:=python
endef

define Package/python3-werkzeug
    $(call Package/python-werkzeug/Default)
    TITLE:=python3-werkzeug
    DEPENDS:=+python3-light +python3-email
    VARIANT:=python3
endef

define Package/python-werkzeug/description
    Werkzeug

    The Python WSGI Utility Library
endef

define Package/python3-werkzeug/description
    $(call Package/python-werkzeug/description)
    Variant for Python 3
endef

$(eval $(call PyPackage,python-werkzeug))
$(eval $(call BuildPackage,python-werkzeug))
$(eval $(call Py3Package,python3-werkzeug))
$(eval $(call BuildPackage,python3-werkzeug))
