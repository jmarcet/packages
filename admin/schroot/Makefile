#
# Copyright (C) 2019 Javier Marcet <javier@marcet.info>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=schroot
PKG_REV:=2ba1e043dbd65c8f08d1d4821393b099af05af15
PKG_VERSION:=1.6.10
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://salsa.debian.org/debian/schroot
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_LICENSE:=GPL
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_FIXUP:=autoreconf gettext-version
PKG_BUILD_DEPENDS:=gettext

include $(INCLUDE_DIR)/autotools.mk
include $(INCLUDE_DIR)/package.mk

define Package/schroot
  SECTION:=admin
  CATEGORY:=Administration
  TITLE:=Securely enter a chroot and run a command or login shell.
  DEPENDS:=+boost +boost-filesystem +boost-iostreams +boost-program_options +boost-regex +libstdcpp \
	+SCHROOT_BTRFS:btrfs-progs +SCHROOT_LOOPBACK:losetup +SCHROOT_LVM:lvm2 +SCHROOT_UUID:libuuid
  URL:=https://salsa.debian.org/debian/schroot
endef

define Package/schroot/description
Securely enter a chroot and run a command or login shell.
endef

define Package/sudo/conffiles
/etc/schroot/
endef

define Package/schroot/config
	source "$(SOURCE)/Config.in"
endef

PKG_CONFIG_DEPENDS := \
	CONFIG_SCHROOT_BTRFS \
	CONFIG_SCHROOT_LOOPBACK \
	CONFIG_SCHROOT_LVM \
	CONFIG_SCHROOT_UUID

CONFIGURE_ARGS += \
	--enable-block-device \
	--enable-union \
	--disable-dchroot \
	--disable-dchroot-dsa \
	--disable-csbuild \
	--disable-debug \
	--disable-pam \
	--disable-doxygen \
	--disable-rpath

ifeq ($(CONFIG_SCHROOT_BTRFS),)
CONFIGURE_ARGS += --disable-btrfs-snapshot
else
CONFIGURE_ARGS += --enable-btrfs-snapshot
endif

ifeq ($(CONFIG_SCHROOT_LOOPBACK),)
CONFIGURE_ARGS += --disable-loopback
else
CONFIGURE_ARGS += --enable-loopback
endif

ifeq ($(CONFIG_SCHROOT_LVM),)
CONFIGURE_ARGS += --disable-lvm-snapshot
else
CONFIGURE_ARGS += --enable-lvm-snapshot
endif

ifeq ($(CONFIG_SCHROOT_UUID),)
CONFIGURE_ARGS += --disable-uuid
else
CONFIGURE_ARGS += --enable-uuid
endif

TARGET_CXXFLAGS += -I$(STAGING_DIR)/usr/lib/libintl-stub/include -fpermissive
TARGET_LDFLAGS += -L$(STAGING_DIR)/usr/lib/libintl-stub/lib

define Package/schroot/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_SUID) $(PKG_INSTALL_DIR)/usr/bin/schroot $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/schroot
	$(CP) -R $(PKG_INSTALL_DIR)/etc/schroot/* $(1)/etc/schroot
	$(INSTALL_DIR) $(1)/usr/lib/schroot
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/libsbuild.* $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/schroot/* $(1)/usr/lib/schroot/
	$(INSTALL_DIR) $(1)/usr/share/schroot
	$(CP) -R $(PKG_INSTALL_DIR)/usr/share/schroot/* $(1)/usr/share/schroot/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/schroot.init $(1)/etc/init.d/schroot
endef

$(eval $(call BuildPackage,schroot))
