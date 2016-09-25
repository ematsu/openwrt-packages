#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libatomic_ops
PKG_VERSION:=7.4.4

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.ivmaisoft.com/_bin/atomic_ops/
PKG_MD5SUM:=426d804baae12c372967a6d183e25af2

PKG_INSTALL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_DEPENDS:=libatomic_ops/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk

define Package/libatomic_ops
    TITLE:=Atomic memory update operation library
    SECTION:=libs
    CATEGORY:=Libraries
    URL:=http://www.ivmaisoft.com/_bin/atomic_ops/
endef

define Package/libatomic_ops/description
    libatomic_ops provides implementations for atomic memory update operations on a number of architectures.
endef

TARGET_CFLAGS += $(FPIC)

CONFIGURE_ARGS += \
        --enable-shared \
        --disable-static \
 
define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include 
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib 
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/libatomic_ops/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libatomic_ops.so* $(1)/usr/lib/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,libatomic_ops))
