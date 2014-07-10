#
# Copyright (C) 2006-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bluez
PKG_VERSION:=5.21
PKG_RELEASE:=5

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=http://www.kernel.org/pub/linux/bluetooth
#PKG_MD5SUM:=8c2ca546c0e7bb73dbd0e906fce7f6b1

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/bluez5
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Bluetooth library
  DEPENDS:=+glib2 +dbus +udev +libncurses +libreadline
  URL:=http://www.bluez.org/
endef
# libreadline undef termcap symbols on debian7
# libncurses for termcap ?

CONFIGURE_ARGS += \
		--prefix=$(1)/usr \
		--enable-shared \
		--enable-static \
		--enable-sixaxis \
		--enable-library \
		--disable-systemd \
	#	--static-libs \

TARGET_CFLAGS += $(FPIC)

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/bluetooth
	$(CP) $(PKG_INSTALL_DIR)/usr/include/bluetooth/*.h $(1)/usr/include/bluetooth
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libbluetooth.{a,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/bluez.pc $(1)/usr/lib/pkgconfig/
endef

define Package/bluez5/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libbluetooth.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,bluez5))
