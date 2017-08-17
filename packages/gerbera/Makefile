#
# Copyright (C) 2011-2017 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gerbera
PKG_VERSION:=1.0
# release v1.0: PKG_REV:=c5491a7a0ea3280294c2144a07b3d1a1b3ba7285
# build HEAD from 14.8.2017
PKG_REV:=d1b1ac6c2ffacf11fdd20d4bac38eda076b9bdca
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/v00d00/gerbera.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/gerbera
	SECTION:=multimedia
	CATEGORY:=Multimedia
	DEPENDS:=+libffmpeg-full +libffmpegthumbnailer +duktape +libupnp-1.8 +libsqlite3 \
	+libcurl +libtheora +file +libexif +libexpat +libvorbis +libuuid +libstdcpp
	TITLE:=a free media server
	URL:=https://gerbera.io
	MAINTAINER:=Entware team, http://entware.net
endef

define Package/gerbera/description
 UPnP Media Server for 2017 (Based on MediaTomb)
endef

# TODO: use taglib
CMAKE_OPTIONS += \
	-DWITH_MAGIC=1 \
	-DWITH_MYSQL=0 \
	-DWITH_CURL=1 \
	-DWITH_JS=1 \
	-DWITH_TAGLIB=0 \
	-DWITH_AVCODEC=1 \
	-DWITH_FFMPEGTHUMBNAILER=1 \
	-DWITH_EXIF=1 \
	-DWITH_LASTFM=0 \
	-DWITH_DEBUG_LOGGING=0

define Package/gerbera/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/share
	$(CP) $(PKG_INSTALL_DIR)/usr/share/$(PKG_NAME) $(1)/usr/share
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) files/$(PKG_NAME).init $(1)/etc/init.d/$(PKG_NAME)
	$(INSTALL_DIR) $(1)/etc/$(PKG_NAME)
	$(CP) files/config.main.xml $(1)/etc/$(PKG_NAME)
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/$(PKG_NAME).conf $(1)/etc/config/$(PKG_NAME)
endef

$(eval $(call BuildPackage,gerbera))
