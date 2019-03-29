#
#
# Copyright (C) 2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mbusd
PKG_VERSION:=0.3.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/3cky/mbusd.git
PKG_SOURCE_VERSION:=650d88a2696a65fc7a6ca4526fbf59027458668f
PKG_MIRROR_HASH:=d5d216a0c6b63bbd28765a3a7248410e727595c994673599643ff3c0371dc83b

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mbusd
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=mbusd modbus gateway
endef

define Package/mbusd/description
 mbusd modbus gateway.
endef

define Package/mbusd/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mbusd $(1)/usr/bin
endef

$(eval $(call BuildPackage,mbusd))
