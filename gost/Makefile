# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=gost
PKG_VERSION:=3.0.0-beta.4-dark
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/kontorol/gost/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=e34bc3a95f9a9de94ee5c4581fe47b5b7a48c71503e3c147d696248ae3f96ba4

PKG_LICENSE:=MIT
PKG_LICENSE_FILE:=LICENSE
PKG_MAINTAINER:=Tianling Shen <cnsztl@immortalwrt.org>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/kontorol/gost
GO_PKG_BUILD_PKG:=github.com/go-gost/gost/cmd/gost

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/gost
  SECTION:=net
  CATEGORY:=Network
  TITLE:=GO Simple Tunnel
  URL:=https://github.com/kontorol/gost
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
endef

define Package/gost/install
	$(call GoPackage/Package/Install/Bin,$(1))

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) $(CURDIR)/files/gost.config $(1)/etc/config/gost
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(CURDIR)/files/gost.init $(1)/etc/init.d/gost
endef

$(eval $(call GoBinPackage,gost))
$(eval $(call BuildPackage,gost))
