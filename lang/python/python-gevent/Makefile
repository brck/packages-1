# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-gevent
PKG_VERSION:=2014-12-14-72119c8c3e704b75a2d91d8555ca8673928ebabb
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/surfly/gevent.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=72119c8c3e704b75a2d91d8555ca8673928ebabb
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_BUILD_DEPENDS:=python python-cython
PKG_USE_MIPS16:=0

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

ifdef CONFIG_USE_MIPS16
	TARGET_CFLAGS += -mno-mips16 -mno-interlink-mips16
endif

define Package/python-gevent
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=http://www.gevent.org/
	DEPENDS:=+python +python-greenlet
endef

define Package/python-gevent
	$(call Package/python-gevent/Default)
	TITLE:=python-gevent
	VARIANT:=python
endef

define Package/python3-gevent
	$(call Package/python-gevent/Default)
	TITLE:=python3-gevent
	VARIANT:=python3
endef

define Package/python-gevent/description
	gevent is a coroutine-based Python networking library.
endef

define Package/python3-gevent/description
	gevent is a coroutine-based Python networking library.
	Variant for Python 3
endef

define Build/Compile
	(cd $(PKG_BUILD_DIR)/libev; \
		$(TARGET_CONFIGURE_OPTS) \
                CFLAGS="$(TARGET_CFLAGS)" \
                CPPFLAGS="-I$(STAGING_DIR)/usr/include -I$(STAGING_DIR)/include" \
                LDFLAGS="-L$(STAGING_DIR)/usr/lib -L$(STAGING_DIR)/lib" \
		$(PKG_BUILD_DIR)/libev/configure \
			--target=$(GNU_TARGET_NAME) \
                        --host=$(GNU_TARGET_NAME) \
                        --build=$(GNU_HOST_NAME) \
                        --prefix=/usr \
                        --without-libiconv-prefix \
                        --without-libintl-prefix \
                        --disable-nls \
	);
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
		CYTHON="$(STAGING_DIR_HOST)/usr/bin/cython" \
	)
endef

$(eval $(call PyPackage,python-gevent))
$(eval $(call BuildPackage,python-gevent))
$(eval $(call Py3Package,python3-gevent))
$(eval $(call BuildPackage,python3-gevent))
