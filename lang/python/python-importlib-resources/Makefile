include $(TOPDIR)/rules.mk

PKG_NAME:=python-importlib-resources
PKG_VERSION:=3.0.0
PKG_RELEASE:=5

PYPI_NAME:=importlib-resources
PYPI_SOURCE_NAME:=importlib_resources
PKG_HASH:=19f745a6eca188b490b1428c8d1d4a0d2368759f32370ea8fb89cad2ab1106c3

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=BRCK <dev@brck.com>

PKG_BUILD_DEPENDS:=python-typing

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-importlib-resources/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python importlib-resources
	URL:=https://importlib-resources.readthedocs.io/en/latest/
endef

define Package/python-importlib-resources
$(call Package/python-importlib-resources/Default)
  DEPENDS:=+python-light +python-singledispatch +python-six +python-contextlib2 \
    +python-pathlib2 +python-scandir +python-typing +python-zipp
  VARIANT:=python
endef

define Package/python3-importlib-resources
$(call Package/python-importlib-resources/Default)
  DEPENDS:=+python3-light +python3-singledispatch +python3-six +python3-contextlib2 \
    +python3-pathlib2 +python3-scandir +python3-typing +python3-zipp
  VARIANT:=python3
endef

define Package/python-importlib-resources/description
  Read resources from Python packages
endef

define Package/python3-importlib-resources/description
$(call Package/python-importlib-resources/description)
.
(Variant for Python3)
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python-importlib-resources/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call PyPackage,python-importlib-resources))
$(eval $(call BuildPackage,python-importlib-resources))
$(eval $(call BuildPackage,python-importlib-resources-src))

$(eval $(call Py3Package,python3-importlib-resources))
$(eval $(call BuildPackage,python3-importlib-resources))
$(eval $(call BuildPackage,python3-importlib-resources-src))
