#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-psutil
PKG_VERSION:=5.2.2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/giampaolo/psutil.git
PKG_SOURCE_VERSION=release-$(PKG_VERSION)
PKG_SOURCE:=psutil-$(PKG_VERSION).tar.gz
PKG_SOURCE_SUBDIR=$(PKG_NAME)-$(PKG_VERSION)

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

define Package/python-psutil/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://pythonhosted.org/psutil/
	MAINTAINER:=BRCK <dev@brck.com>
endef

define Package/python-psutil
	$(call Package/python-psutil/Default)
	TITLE:=python-psutil
	VARIANT:=python
	DEPENDS:=+python
endef

define Package/python3-psutil
	$(call Package/python-psutil/Default)
	TITLE:=python3-psutil
	VARIANT:=python3
	DEPENDS:=+python3
endef

define Package/python-psutil/description
psutil is a module providing an interface for retrieving information on all
running processes and system utilization (CPU, memory, disks, network, users)
in a portable way by using Python.
endef

define Package/python3-psutil/description
	$(call Package/python-psutil/description)
	Variant for Python 3.
endef

$(eval $(call PyPackage,python-psutil))
$(eval $(call BuildPackage,python-psutil))
$(eval $(call Py3Package,python3-psutil))
$(eval $(call BuildPackage,python3-psutil))
