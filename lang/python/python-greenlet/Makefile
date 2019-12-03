#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=python-greenlet
PKG_VERSION:=0.4.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/python-greenlet/greenlet.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
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

define Package/python-greenlet/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/python-greenlet/greenlet
	MAINTAINER:=BRCK <dev@brck.com>
endef


define Package/python-greenlet
	$(call Package/python-greenlet/Default)
	TITLE:=python-greenlet
	VARIANT:=python
endef

define Package/python3-greenlet
	$(call Package/python-greenlet/Default)
	TITLE:=python3-greenlet
	VARIANT:=python3
endef

define Package/python-greenlet/description
        The greenlet package is a spin-off of Stackless, a version of CPython
        that supports micro-threads called "tasklets". Tasklets run
        pseudo-concurrently (typically in a single or a few OS-level threads)
        and are synchronized with data exchanges on "channels".

        A "greenlet", on the other hand, is a still more primitive notion of
        micro-thread with no implicit scheduling; coroutines, in other
        words. This is useful when you want to control exactly when your code
        runs. You can build custom scheduled micro-threads on top of greenlet;
        however, it seems that greenlets are useful on their own as a way to
        make advanced control flow structures. For example, we can recreate
        generators; the difference with Python's own generators is that our
        generators can call nested functions and the nested functions can
        yield values too. Additionally, you don't need a "yield" keyword. See
        the example in tests/test_generator.py.

        Greenlets are provided as a C extension module for the regular
        unmodified interpreter.

        Greenlets are lightweight coroutines for in-process concurrent
        programming.
endef

define Package/python3-greenlet/description
	$(call Package/python-greenlet/description)
	Variant for Python 3.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix="$(PKG_INSTALL_DIR)/usr")
endef

define Package/python-greenlet/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)/usr/* \
	    $(1)/usr/
endef

$(eval $(call BuildPackage,python-greenlet))