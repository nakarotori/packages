#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=opus
PKG_VERSION:=1.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://downloads.xiph.org/releases/opus
PKG_MD5SUM:=c5a8cf7c0b066759542bc4ca46817ac6

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILE:=COPYING
PKG_MAINTAINER:=Dirk Neukirchen <dirkneukirchen@web.de>

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk


define Package/libopus
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Opus codec library
  URL:=http://www.opus-codec.org
endef

define Package/libopus/description
  The Opus codec is designed to handle a wide range of interactive
  audio applications, including Voice over IP, videoconferencing,
  in-game chat, and even remote live music performances. It can scale
  from low bit-rate narrowband speech to very high quality stereo music.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/opus.pc $(1)/usr/lib/pkgconfig/
	$(INSTALL_DIR) $(1)/usr/include/opus
	$(CP) $(PKG_INSTALL_DIR)/usr/include/opus/*.h $(1)/usr/include/opus/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libopus.* $(1)/usr/lib/
endef

define Package/libopus/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/libopus.so.* $(1)/usr/lib/
endef


$(eval $(call BuildPackage,libopus))
