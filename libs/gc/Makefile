#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gc
PKG_VERSION:=7.6.0

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.hboehm.info/gc/gc_source/
PKG_MD5SUM:=bf46ccbdaccfa3186c2ab87191c8855a

PKG_INSTALL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_DEPENDS:=gc/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk

define Package/gc
    TITLE:=Gabage collector
    SECTION:=libs
    CATEGORY:=Libraries
    URL:=http://www.linuxfromscratch.org/blfs/view/svn/general/gc.html
    DEPENDS:=+libpthread +libatomic_ops 
endef

define Package/gc/description
    The GC package contains the Boehm-Demers-Weiser conservative garbage collector, which can be used as a garbage collecting replacement for the C malloc function or C++ new operator. 
endef

TARGET_CFLAGS+="-I./include"

TARGET_LDFLAGS+=-lpthread -latomic_ops

CONFIGURE_ARGS += \
	--disable-gcj-support \
	--disable-java-finalization \
	--disable-atomic-uncollectible \


define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include 
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib 
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig $(1)/usr/lib/
endef

define Package/gc/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{cord,gc}.so* $(1)/usr/lib/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,gc))
