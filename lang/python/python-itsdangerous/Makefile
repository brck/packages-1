# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-itsdangerous
PKG_VERSION:=1.1.0
PKG_RELEASE:=2

PKG_SOURCE:=itsdangerous-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/68/1a/f27de07a8a304ad5fa817bbe383d1238ac4396da447fa11ed937039fa04b
PKG_HASH:=321b033d07f2a4136d3ec762eac9f16a10ccd60f53c0c91af90217ace7ba1f19

PKG_BUILD_DIR:=$(BUILD_DIR)/itsdangerous-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Daniel Golle <daniel@makrotopia.org>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-$(PKG_NAME)-$(PKG_VERSION)
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

define Package/python-itsdangerous/Default
    SECTION:=lang
    CATEGORY:=Languages
    SUBMENU:=Python
    URL:=http://github.com/mitsuhiko/itsdangerous
endef

define Package/python-itsdangerous
    $(call Package/python-itsdangerous/Default)
    TITLE:=python-itsdangerous
    DEPENDS:=+python-light
    VARIANT:=python3
endef

define Package/python3-itsdangerous
    $(call Package/python-itsdangerous/Default)
    TITLE:=python3-itsdangerous
    DEPENDS:=+python3-light
    VARIANT:=python3
endef

define Package/python-itsdangerous/description
    Various helpers to pass trusted data to untrusted environments and back.
endef

define Package/python3-itsdangerous/description
	$(call Package/python-itsdangerous/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-itsdangerous))
$(eval $(call BuildPackage,python-itsdangerous))
$(eval $(call Py3Package,python3-itsdangerous))
$(eval $(call BuildPackage,python3-itsdangerous))

