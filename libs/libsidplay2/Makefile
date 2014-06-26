#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libsidplay2
PKG_VERSION:=2.1.1
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/sidplay-libs-$(PKG_VERSION)
PKG_SOURCE:=sidplay-libs-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/sidplay2
PKG_MD5SUM:=7ea0ba5dc1da4604d15eaae001f7d2a7

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=COPYING

PKG_MAINTAINER:=Dirk Neukirchen <dirkneukirchen@web.de>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk


define Package/libsidplay2
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=c64 sid library
  DEPENDS:=+libstdcpp
endef

define Package/libsidplay2/description
libsid is used by mpd
endef

TARGET_LDFLAGS += \
        -Wl,-rpath-link,$(STAGING_DIR)/usr/lib

CONFIGURE_ARGS+= \
        --host=$(GNU_TARGET_NAME) \
        --build=$(GNU_HOST_NAME) \
        --prefix="/usr/share/$(PKG_NAME)" \
        --bindir="/usr/bin" \
        --libdir="/usr/lib" \
        --sysconfdir="/etc/$(PKG_NAME)"

define Package/libsidplay2/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libsidplay/src/.libs/libsidplay2.so* $(1)/usr/lib/
endef


$(eval $(call BuildPackage,libsidplay2))
