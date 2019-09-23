include $(TOPDIR)/rules.mk

PKG_NAME:=python-flask-socketio
PKG_VERSION:=4.1.0
PKG_RELEASE:=2

PKG_SOURCE:=Flask-SocketIO-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/6f/e6/9c0bc9f6e1672ef684d7328c1bb5bdd5ff298c484d604fea5cb79d44495a
PKG_HASH:=aced332903522a52822fb1e21744549510ce8b26e074422d4cd9aff68e43be5b

PKG_BUILD_DIR:=$(BUILD_DIR)/Flask-SocketIO-$(PKG_VERSION)
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

define Package/python-flask-socketio
	SECTION:=language-python
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=Python Flask-SocketIO
	URL:=https://github.com/miguelgrinberg/Flask-SocketIO
	MAINTAINER:=Edoardo Biraghi <edoardo@brck.com>
	DEPENDS:=+python +python-flask +python-socketio
endef

define Package/python-flask-socketio/description
	Socket.IO integration for Flask applications. 
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-flask-socketio/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python-flask-socketio))
