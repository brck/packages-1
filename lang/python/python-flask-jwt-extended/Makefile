include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-jwt-extended
PKG_VERSION:=3.24.1
PKG_RELEASE:=1

PKG_SOURCE:=Flask-JWT-Extended-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/7a/ee/bb1c679b44ebec5c64626d632186d890cd95fffb63c1bded85d979a80724
PKG_HASH:=0aa8ee6fa7eb3be9314e39dd199ac8e19389a95371f9d54e155c7aa635e319dd

PKG_BUILD_DIR:=$(BUILD_DIR)/Flask-JWT-Extended-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python python-setuptools

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

define Package/python-flask-jwt-extended/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://github.com/vimalloc/flask-jwt-extended
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python \
		+python-flask \
		+python-pyjwt
endef

define Package/python-flask-jwt-extended
  $(call Package/python-flask-jwt-extended/Default)
  TITLE:=python-flask-jwt-extended
  VARIANT:=python
endef

define Package/python-flask-jwt-extended/description
	An open source Flask extension that provides JWT support (with batteries included)!
endef

$(eval $(call PyPackage,python-flask-jwt-extended))
$(eval $(call BuildPackage,python-flask-jwt-extended))
