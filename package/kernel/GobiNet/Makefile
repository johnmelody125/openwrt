#
# Copyright (C) 2008-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk
 
PKG_NAME:=GobiNet
PKG_RELEASE:=1
 
include $(INCLUDE_DIR)/package.mk
 
define KernelPackage/GobiNet
    SUBMENU:=Other modules
    TITLE:=Support Module for GobiNet
    DEPENDS:=+kmod-usb-core +kmod-usb-net
    FILES:=$(PKG_BUILD_DIR)/GobiNet.ko
    AUTOLOAD:=$(call AutoLoad,91,GobiNet)
endef
 
define KernelPackage/GobiNet/description
    This is Longsun LTE module Gobinet drivers
endef
 
MAKE_OPTS:=ARCH="$(LINUX_KARCH)" \
    CROSS_COMPILE="$(TARGET_CROSS)" \
    SUBDIRS="$(PKG_BUILD_DIR)"
    
define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef
 
define Build/Compile
    $(KERNEL_MAKE)  M="$(PKG_BUILD_DIR)" $(MAKE_OPTS) modules
endef
 
$(eval $(call KernelPackage,GobiNet))