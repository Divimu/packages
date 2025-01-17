# SPDX-Identifier-License: GPL-3.0-only
#
# Copyright (C) 2022 Lean <coolsnowwolf@gmail.com>
# Copyright (C) 2019-2024 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-turboacc
PKG_FLAGS:=nonshared

PKG_LICENSE:=GPL-3.0-only
PKG_MAINTAINER:=Lean <coolsnowwolf@gmail.com>

PKG_CONFIG_DEPENDS:= \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_BBR_CCA \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_DNSFORWARDER \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_DNSPROXY \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_OFFLOADING

LUCI_TITLE:=LuCI support for Flow Offload / Shortcut-FE
LUCI_DEPENDS:=+PACKAGE_$(PKG_NAME)_INCLUDE_BBR_CCA:kmod-tcp-bbr \
	+PACKAGE_$(PKG_NAME)_INCLUDE_OFFLOADING:kmod-ipt-offload
LUCI_PKGARCH:=all

define Package/$(PKG_NAME)/config
config PACKAGE_$(PKG_NAME)_INCLUDE_OFFLOADING
	bool "Include Flow Offload"
	default y if !(TARGET_ipq40xx||TARGET_ipq806x||TARGET_qualcommax)

config PACKAGE_$(PKG_NAME)_INCLUDE_BBR_CCA
	bool "Include BBR CCA"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_PDNSD
	bool "Include Pdnsd"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_DNSFORWARDER
	bool "Include DNSForwarder"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_DNSPROXY
	bool "Include DNSProxy"
	default n
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
