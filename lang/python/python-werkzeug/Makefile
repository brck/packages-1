# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-werkzeug
PKG_VERSION:=1.0.1
PKG_RELEASE:=2

PKG_SOURCE:=Werkzeug-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/10/27/a33329150147594eff0ea4c33c2036c0eadd933141055be0ff911f7f8d04
PKG_HASH:=6c80b1e5ad3665290ea39320b91e1be1e0d5f60652b964a3070216de83d2e47c

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
