#
# Copyright (C) 2011-2020 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=upx
PKG_VERSION:=5.2.1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-src.tar.xz
PKG_SOURCE_URL:=https://github.com/upx/upx/releases/download/v$(PKG_VERSION)/
PKG_HASH:=skip

HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/$(PKG_NAME)-$(PKG_VERSION)-src
HOST_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/host-build.mk

define Host/Compile
	$(MAKE) -C $(HOST_BUILD_DIR)/src \
		LDFLAGS="$(HOST_LDFLAGS)" \
		CXX="$(HOSTCXX)"
endef

define Host/Install
	$(INSTALL_DIR) $(STAGING_DIR_HOST)/bin
	$(INSTALL_BIN) $(HOST_BUILD_DIR)/build/release/upx $(STAGING_DIR_HOST)/bin/upx
endef

define Host/Clean
	rm -f $(STAGING_DIR_HOST)/bin/upx
endef

$(eval $(call HostBuild))
