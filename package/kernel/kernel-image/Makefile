#
# Copyright (C) 2009-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/image.mk

PKG_NAME:=kernel-image

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=

PKG_MAINTAINER:=John Crispin <john@phrozen.org>

include $(INCLUDE_DIR)/package.mk

define Package/kernel-image
  SECTION:=kernel
  CATEGORY:=Kernel image
  URL:=http://www.kernel.org/
  TITLE:=Kernel Image
  VERSION:=$(LINUX_VERSION)-$(LINUX_RELEASE)-$(LINUX_VERMAGIC)
  DEPENDS:=@TARGET_brcm2708_bcm2710 +libc +libstdcpp +zlib
  DEFAULT:=m if TARGET_brcm2708_bcm2710
endef

define Package/kernel-image/description
  Binary files for kernel image
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/kernel-image/install
	$(INSTALL_DIR) $(1)/boot
	$(INSTALL_DIR) $(1)/boot/overlays

	$(INSTALL_DATA) \
		$(KDIR)/Image $(1)/boot/kernel.img

	$(INSTALL_DATA) \
		$(DTS_DIR)/overlays/*.dtbo $(1)/boot/overlays
endef

$(eval $(call BuildPackage,kernel-image))
