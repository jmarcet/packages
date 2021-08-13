#
# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=jq
PKG_RELEASE:=1
PKG_LICENSE:=BSD

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/stedolan/jq.git
PKG_SOURCE_DATE:=2021-05-01
PKG_SOURCE_VERSION:=d18b2d078c2383d9472d0a0a226e07009025574f
PKG_MIRROR_HASH:=b8f4360a5b005d78df4d9eb23e0e467fe0438afc1d73a8e4e78b4b2d2bb2e243

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

ifdef CONFIG_USE_MIPS16
  TARGET_CFLAGS += -fno-ipa-sra
endif

TARGET_CFLAGS += -std=c99 -D_GNU_SOURCE

CONFIGURE_ARGS+= \
	--disable-docs \
	--disable-valgrind \
	--without-oniguruma

define Package/jq
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Lightweight and flexible command-line JSON processor.
  URL:=https://stedolan.github.io/jq/
  MAINTAINER:=Marko Ratkaj <marko.ratkaj@sartura.hr>
endef

define Package/jq/description
	Lightweight and flexible command-line JSON processor.
endef

define Package/jq/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
endef

$(eval $(call BuildPackage,jq))
