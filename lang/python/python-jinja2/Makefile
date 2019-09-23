include $(TOPDIR)/rules.mk

PKG_NAME:=python-jinja2
PKG_VERSION:=2.10.1
PKG_RELEASE:=2

PKG_SOURCE:=Jinja2-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/93/ea/d884a06f8c7f9b7afbc8138b762e80479fb17aedbbe2b06515a12de9378d
PKG_SHA256SUM:=065c4f02ebe7f7cf559e49ee5a95fb800a9e4528727aec6f24402a5374c65013

PKG_BUILD_DIR:=$(BUILD_DIR)/Jinja2-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python python3

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

define Package/python-jinja2/Default
    SECTION:=lang
    CATEGORY:=Languages
    SUBMENU:=Python
    URL:=http://jinja.pocoo.org/
endef

define Package/python-jinja2
    $(call Package/python-jinja2/Default)
    TITLE:=python-jinja2
    DEPENDS:=+python-light +python-markupsafe
    VARIANT:=python
endef

define Package/python3-jinja2
    $(call Package/python-jinja2/Default)
    TITLE:=python3-jinja2
    DEPENDS:=+python3-light +python3-markupsafe
    VARIANT:=python3
endef

define Package/python-jinja2/description
    Jinja2 is a full featured template engine for Python. It has full
    unicode support, an optional integrated sandboxed execution
    environment, widely used and BSD licensed.
endef


define Package/python3-jinja2/description
    $(call Package/python-jinja2/description)
    Variant for Python 3.
endef

$(eval $(call PyPackage,python-jinja2))
$(eval $(call BuildPackage,python-jinja2))
$(eval $(call BuildPackage,python-jinja2-src))
$(eval $(call Py3Package,python3-jinja2))
$(eval $(call BuildPackage,python3-jinja2))
$(eval $(call BuildPackage,python3-jinja2-src))
