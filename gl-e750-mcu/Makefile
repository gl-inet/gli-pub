
#
# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=gl-e750-mcu
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/gl-inet/GL-E750-MCU-instruction.git
PKG_SOURCE_DATE:=2020-06-08
PKG_SOURCE_VERSION:=f8c77bdb2ba4e78571b9a41af87a8ab2586679f4

include $(INCLUDE_DIR)/package.mk

PKG_CONFIG_DEPENDS += CONFIG_BUSYBOX_DEFAULT_TIMEOUT

define Package/gl-e750-mcu/Default
	SECTION:=base
	CATEGORY:=gl-inet
	TITLE:=GL iNet mcu interface
	DEPENDS:=+libjson-c +libpthread +libuci +libcurl +libblobmsg-json +libiwinfo +libubox +libubus +libuuid  
endef

Package/gl-e750-mcu = $(Package/gl-e750-mcu/Default)

define Package/gl-e750-mcu/description
gl mcu data interface for gl-inet.
endef


define Build/Prepare
	$(Build/Prepare/Default)
	$(CP) $(PKG_BUILD_DIR)/src/* $(PKG_BUILD_DIR)
	$(CP) $(PKG_BUILD_DIR)/files/* $(PKG_BUILD_DIR)
endef

define Package/gl-e750-mcu/install	
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/e750-mcu $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mcu_update $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/e750_mcu $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mcu_shutdown $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/mcu $(1)/etc/config
	$(INSTALL_DIR) $(1)/etc/hotplug.d/ntp
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/01-check_sync $(1)/etc/hotplug.d/ntp
	$(INSTALL_DIR) $(1)/etc/hotplug.d/iface
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/18-mcu-notify $(1)/etc/hotplug.d/iface
	$(INSTALL_DIR) $(1)/usr/lib/gl
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/libglmcu.so $(1)/usr/lib/gl
	$(LN) /usr/lib/gl/libglmcu.so $(1)/usr/lib/
	
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/controller/admin/
	$(CP) $(PKG_BUILD_DIR)/luci/control/* $(1)/usr/lib/lua/luci/controller/admin/
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/model/cbi/admin_system/
	$(CP) $(PKG_BUILD_DIR)/luci/cbi/* $(1)/usr/lib/lua/luci/model/cbi/admin_system/
	
endef

$(eval $(call BuildPackage,gl-e750-mcu))
