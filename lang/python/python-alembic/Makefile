include $(TOPDIR)/rules.mk

PKG_NAME:=python-alembic
PKG_VERSION:=1.0.11
PKG_RELEASE:=2

PKG_SOURCE:=alembic-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/7b/8b/0c98c378d93165d9809193f274c3c6e2151120d955b752419c7d43e4d857
PKG_HASH:=cdb7d98bd5cbf65acd38d70b1c05573c432e6473a82f955cdea541b5c153b0cc

PKG_BUILD_DIR:=$(BUILD_DIR)/alembic-$(PKG_VERSION)
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


define Package/python-alembic/Default
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	URL:=https://alembic.sqlalchemy.org/
	MAINTAINER:=BRCK <dev@brck.com>
	DEPENDS:=+python +python-mako +python-dateutil +python-editor +python-sqlalchemy
endef

define Package/python-alembic
        $(call Package/python-alembic/Default)
        TITLE:=python-alembic
        VARIANT:=python
endef

define Package/python-alembic/description
	Alembic is a database migrations tool written by the author of SQLAlchemy. 
endef

$(eval $(call PyPackage,python-alembic))
$(eval $(call BuildPackage,python-alembic))
