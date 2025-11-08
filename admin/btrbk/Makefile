include $(TOPDIR)/rules.mk

PKG_NAME:=btrbk
PKG_VERSION:=0.33.0-dev
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/digint/btrbk.git
PKG_SOURCE_VERSION:=ba3c36c984bafda41c32623a645096780eb724d9
PKG_MIRROR_HASH:=20526a130bc5af99616ca99cff707331cc78230abdbb5825c04190889fa8c209

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

define Package/btrbk
  SECTION:=admin
  CATEGORY:=Administration
  TITLE:=Backup tool for btrfs subvolumes with atomic snapshots & incremental transfers
  URL:=https://digint.ch/btrbk/
  DEPENDS:=+btrfs-progs +perl +perlbase-getopt +perlbase-ipc +perlbase-time
endef

define Package/btrbk/description
  btrbk is a backup tool for btrfs subvolumes, taking advantage of btrfs specific
  capabilities to create atomic snapshots and transfer them incrementally to your
  backup locations.
endef

define Build/Compile
	true
endef

define Package/btrbk/install
	$(INSTALL_DIR) $(strip $(1))/etc
	$(INSTALL_DIR) $(strip $(1))/usr/bin

	$(INSTALL_BIN) $(PKG_BUILD_DIR)/btrbk $(strip $(1))/usr/bin
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/btrbk.conf.example $(strip $(1))/etc/btrbk.conf
	$(LN) btrbk $(1)/usr/bin/lsbtr
endef

$(eval $(call BuildPackage,btrbk))
