#
# Copyright (C) 2011-2017 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=duktape
PKG_VERSION:=2.1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=http://duktape.org
PKG_HASH:=e02364cd72077e34e204b8375c8bd7c461eb13cb623c7dc1a74d253d84b1446b

PKG_INSTALL :=1

include $(INCLUDE_DIR)/package.mk

define Package/duktape
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=JavaScript
	DEPENDS:=+libreadline +libncurses
	TITLE:=Duktape JavaScript engine
	URL:=$(PKG_SOURCE_URL)
	MAINTAINER:=Entware team, http://entware.net
endef

define Package/duktape/description
 Duktape is an embeddable Javascript engine, with a focus on portability and
 compact footprint.
endef

define Build/Prepare
	$(call Build/Prepare/Default)
	$(CP) $(PKG_BUILD_DIR)/Makefile.sharedlibrary $(PKG_BUILD_DIR)/Makefile
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/include/*.h $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/lib/libduktape.so* $(1)/usr/lib
endef

define Package/duktape/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/lib/libduktape.so* $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/duk $(1)/usr/bin
	$(LN) duk $(1)/usr/bin/js
endef

$(eval $(call BuildPackage,duktape))
