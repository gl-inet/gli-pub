#
# Copyright (C) 2008-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=nsh
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

define KernelPackage/nsh
  SUBMENU:=Other modules
  TITLE:=Network Service Header (NSH) protocol
  FILES:=$(LINUX_DIR)/net/nsh/nsh.ko
  AUTOLOAD:=$(call AutoLoad,13,nsh)
  KCONFIG:=CONFIG_NET_NSH
endef

define KernelPackage/nsh/description
  Network Service Header is an implementation of Service Function
  Chaining (RFC 7665).  Requires kernel 4.14 or newer
endef

define Build/Compile
endef

$(eval $(call KernelPackage,nsh))
