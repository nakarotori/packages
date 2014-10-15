#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# Contributors:   nakarotori & construct.io
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libical
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://downloads.sourceforge.net/freeassociation

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libical
  SECTION:=libs
  CATEGORY:=Libraries
  SUBMENU:=ical
  DEPENDS:=+libstdcpp +libpthread
  TITLE:=iCalendar Specification Library
  URL:=http://www.sourceforge.net/projects/libical/
endef

CONFIGURE_ARGS += \
		--enable-shared \
		--enable-static \

TARGET_CFLAGS += $(FPIC)

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/ical.h $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libical/ $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libical*.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libical.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libical/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libical*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libical))
