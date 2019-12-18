#
# Copyright (C) 2007-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=coova-chilli
PKG_VERSION:=1.5
PKG_RELEASE:=11

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/coova/coova-chilli/tar.gz/$(PKG_VERSION)?
PKG_HASH:=75e15fd00a870b8a95df1440977c688a05a109f90b57bf679b931101d427d0fb

PKG_MAINTAINER:=Jaehoon You <teslamint@gmail.com>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=0

PKG_CONFIG_DEPENDS:= \
  COOVACHILLI_MINIPORTAL \
  COOVACHILLI_REDIR \
  COOVACHILLI_USERAGENT \
  COOVACHILLI_DNSLOG \
  COOVACHILLI_UAMDOMAINFILE \
  COOVACHILLI_LARGELIMITS \
  COOVACHILLI_NOSSL \
  COOVACHILLI_WOLFSSL \
  COOVACHILLI_OPENSSL

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/kernel.mk

define Package/coova-chilli
  SUBMENU:=Captive Portals
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+kmod-tun +librt +COOVACHILLI_WOLFSSL:libwolfssl +COOVACHILLI_OPENSSL:libopenssl
  TITLE:=Wireless LAN HotSpot controller (Coova Chilli Version)
  URL:=https://coova.github.io/
  MENU:=1
endef

define Package/coova-chilli/description
	CoovaChilli is an open source access controller for wireless LAN
	access points and is based on ChilliSpot. It is used for authenticating
	users of a wireless (or wired) LAN. It supports web based login (UAM)
	which is today's standard for public HotSpots and it supports Wireless
	Protected Access (WPA) which is the standard of the future.
	Authentication,	authorization and accounting (AAA) is handled by your
	favorite radius server.
endef

define Package/coova-chilli/config
  source "$(SOURCE)/Config.in"
endef

define KernelPackage/ipt-coova
  URL:=http://www.coova.org/CoovaChilli
  SUBMENU:=Netfilter Extensions
  DEPENDS:=coova-chilli +kmod-ipt-core +libxtables
  TITLE:=Coova netfilter module
  FILES:=$(PKG_BUILD_DIR)/src/linux/xt_*.$(LINUX_KMOD_SUFFIX)
  AUTOLOAD:=$(call AutoProbe,xt_coova)
endef

define KernelPackage/ipt-coova/description
	Netfilter kernel module for CoovaChilli
	Includes:
	- coova
endef

DISABLE_NLS=

TARGET_CFLAGS += $(FPIC) -Wno-address-of-packed-member

CONFIGURE_VARS += \
       ARCH="$(LINUX_KARCH)" \
       KERNEL_DIR="$(LINUX_DIR)"

MAKE_FLAGS += \
       ARCH="$(LINUX_KARCH)" \
       KERNEL_DIR="$(LINUX_DIR)"

MAKE_INSTALL_FLAGS += \
       ARCH="$(LINUX_KARCH)" \
       KERNEL_DIR="$(LINUX_DIR)" \
       INSTALL_MOD_PATH="$(PKG_INSTALL_DIR)"

define Build/Prepare
$(call Build/Prepare/Default)
	( cd $(PKG_BUILD_DIR) ; \
		[ -f ./configure ] || { \
			./bootstrap ; \
		} \
	)
endef

define Build/Configure
	$(call Build/Configure/Default, \
	$(if $(CONFIG_COOVACHILLI_PROXY),--enable,--disable)-chilliproxy \
	$(if $(CONFIG_COOVACHILLI_REDIR),--enable,--disable)-chilliredir \
	$(if $(CONFIG_COOVACHILLI_DNSLOG),--enable,--disable)-dnslog \
	$(if $(CONFIG_COOVACHILLI_MINIPORTAL),--enable,--disable)-miniportal \
	$(if $(CONFIG_COOVACHILLI_USERAGENT),--enable,--disable)-useragent \
	$(if $(CONFIG_COOVACHILLI_LARGELIMITS),--enable,--disable)-largelimits \
	$(if $(CONFIG_COOVACHILLI_UAMDOMAINFILE),--enable,--disable)-uamdomainfile \
	$(if $(CONFIG_IPV6),--with,--without)-ipv6 \
	$(if $(CONFIG_COOVACHILLI_WOLFSSL),--with,--without)-cyassl \
	$(if $(CONFIG_COOVACHILLI_OPENSSL),--with,--without)-openssl \
	$(if $(CONFIG_PACKAGE_kmod-ipt-coova),--with-nfcoova) \
	--enable-authedallowed \
	--enable-gardenaccounting \
	--enable-statusfile \
	--enable-binstatusfile \
	--enable-forcedns \
	--enable-dhcpopt \
	)
endef

define Package/coova-chilli/conffiles
/etc/config/chilli
endef


define Package/coova-chilli/preinst
	#!/bin/sh
	[ -n "$$IPKG_INSTROOT" ] && exit 0
	[ -x /etc/init.d/chilli-monitor ] && /etc/init.d/chilli-monitor stop 2>/dev/null
	[ -x /etc/init.d/chilli ] && /etc/init.d/chilli stop 2>/dev/null
	# Backup
	[ -f /etc/init.d/chilli-monitor ] && {
		mkdir /etc/chilli-backup
		cp /etc/chilli/defaults /etc/chilli-backup/default
		cp /etc/chilli/up.sh /etc/chilli-backup/up.sh
		cp /etc/config/chilli /etc/chilli-backup/chilli.config
		cp /etc/hotplug.d/iface/30-chilli /etc/chilli-backup/30-chilli
		cp /etc/init.d/chilli /etc/chilli-backup/chilli.init
	}
	exit 0
endef

define Package/coova-chilli/install
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/etc/chilli.conf $(1)/etc/
	$(INSTALL_DIR) $(1)/etc/chilli
	$(CP) $(PKG_INSTALL_DIR)/etc/chilli/* $(1)/etc/chilli/
	$(INSTALL_DIR) $(1)/etc/hotplug.d/iface
	$(INSTALL_DATA) ./files/chilli.hotplug $(1)/etc/hotplug.d/iface/30-chilli
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/chilli* $(1)/usr/sbin/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib*.so.* $(1)/usr/lib/
	$(if $(CONFIG_PACKAGE_kmod-ipt-coova), \
		$(INSTALL_DIR) $(1)/usr/lib/iptables; \
		$(CP) $(PKG_INSTALL_DIR)/usr/lib/iptables/lib*.so $(1)/usr/lib/iptables/ \
	)
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) files/chilli.init $(1)/etc/init.d/chilli
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) files/chilli.config $(1)/etc/config/chilli
	$(INSTALL_DIR) $(1)/lib/firewall
endef


define Package/coova-chilli/postinst
	#!/bin/sh
	[ -n "$$IPKG_INSTROOT" ] && exit 0
	# Restore
	[ -d /etc/chilli-backup ] && {
		cp /etc/chilli-backup/default /etc/chilli/defaults
		cp /etc/chilli-backup/up.sh /etc/chilli/up.sh
		cp /etc/chilli-backup/chilli.config /etc/config/chilli
		cp /etc/chilli-backup/30-chilli /etc/hotplug.d/iface/30-chilli
		cp /etc/chilli-backup/chilli.init /etc/init.d/chilli
		rm -rf /etc/chilli-backup
	}
	/etc/init.d/chilli restart 2>/dev/null
	[ -x /etc/init.d/chilli-monitor ] && {
		/etc/init.d/chilli-monitor restart 2>/dev/null
	}
	exit 0
endef

$(eval $(call BuildPackage,coova-chilli))
$(eval $(call KernelPackage,ipt-coova))
