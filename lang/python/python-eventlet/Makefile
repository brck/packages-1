# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-eventlet
PKG_VERSION:=0.18.4
PKG_RELEASE:=1

PKG_SOURCE:=eventlet-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/e/eventlet/
PKG_MD5SUM:=8d1c646d8cc10a4958c92fe8a30f3676

PKG_BUILD_DIR:=$(BUILD_DIR)/eventlet-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

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

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-eventlet
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://pypi.python.org/pypi/eventlet/
endef
 
define Package/python-eventlet
	$(call Package/python-eventlet/Default)
	TITLE:=python-eventlet
	VARIANT:=python
endef

define Package/python3-eventlet
	$(call Package/python-eventlet/Default)
	TITLE:=python3-eventlet
	VARIANT:=python3
endef

define Package/python-eventlet/description
	A concurrent networking library.
endef

define Package/python3-eventlet/description
	A concurrent networking library.
	Variant for Python 3
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-eventlet/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

define PyPackage/python3-eventlet/install
	:
endef

$(eval $(call PyPackage,python-eventlet))
$(eval $(call BuildPackage,python-eventlet))
$(eval $(call Py3Package,python3-eventlet))
$(eval $(call BuildPackage,python3-eventlet))
