#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=udpxy
PKG_REV:=1.0.23
PKG_TAG:=9
PKG_VERSION:=$(PKG_REV)-$(PKG_TAG)
PKG_RELEASE:=4

PKG_SOURCE:=$(PKG_NAME).$(PKG_REV)-$(patsubst %,%-prod,$(PKG_TAG)).tar.gz
PKG_SOURCE_URL:=http://www.udpxy.com/download/1_23
PKG_MD5SUM:=0c953f7dd80329c1a062997afb9b6744
PKG_MAINTAINER:=Álvaro Fernández Rojas <noltari@gmail.com>

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/udpxy
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Convert UDP IPTV streams into HTTP streams
  URL:=http://www.udpxy.com/index-en.html
endef

define Package/udpxy/description
	udproxy makes it possible to convert UDP IPTV streams into HTTP
	streams which can be viewed even over WLANs. HTTP streams do
	not generate huge amounts of multicast traffic, so a sd stream
	only takes about 300k. Interesting for peoply who have IPTV at
	home and do not want to rent multiple decoders from their
	provider but just use their own streaming client (for example
	popcornhour/mediatomb/vlc).
endef

define Package/udpxy/conffiles
/etc/config/udpxy
endef

MAKE_FLAGS += \
	INSTALLROOT="$(PKG_INSTALL_DIR)/usr" \
	ALL_CFLAGS="$(TARGET_CFLAGS) $(TARGET_CPPFLAGS)"

define Package/udpxy/install
	$(INSTALL_DIR) $(1)/etc/init.d $(1)/etc/config
	$(INSTALL_CONF) ./files/udpxy.conf $(1)/etc/config/udpxy
	$(INSTALL_BIN) ./files/udpxy.init $(1)/etc/init.d/udpxy
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/udpxy $(1)/usr/bin/
	ln -sf udpxy $(1)/usr/bin/udpxrec
endef

$(eval $(call BuildPackage,udpxy))
