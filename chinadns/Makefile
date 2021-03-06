#
# Copyright (C) 2014-2018 OpenWrt-dist
# Copyright (C) 2014-2018 Jian Chang <aa65535@live.com>
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ChinaDNS
PKG_VERSION:=1.3.2
PKG_RELEASE:=8

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/aa65535/ChinaDNS.git
PKG_SOURCE_VERSION:=5ed537bd24b7fd53540799f9ab4cf56f749c3245
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.xz
PKG_MIRROR_HASH:=d4bbb2785b3378d113411872570702e0c30bbed06450230d76ccaef2ab7d2e94

PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jian Chang <aa65535@live.com>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION)

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_USE_MIPS16:=0
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/ChinaDNS
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Protect yourself against DNS poisoning in China.
	URL:=https://github.com/shadowsocks/ChinaDNS
endef

define Package/ChinaDNS/description
Protect yourself against DNS poisoning in China.
endef

define Package/ChinaDNS/conffiles
/etc/config/chinadns
/etc/chinadns_chnroute.txt
endef

define Package/ChinaDNS/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/chinadns.init $(1)/etc/init.d/chinadns
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/chnroute.txt $(1)/etc/chinadns_chnroute.txt
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/chinadns.config $(1)/etc/config/chinadns
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/chinadns $(1)/usr/bin
endef

$(eval $(call BuildPackage,ChinaDNS))
