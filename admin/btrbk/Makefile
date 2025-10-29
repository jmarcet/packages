include $(TOPDIR)/rules.mk

PKG_NAME:=btrbk
PKG_VERSION:=0.32.6
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://digint.ch/download/btrbk/releases/
PKG_HASH:=02e2ac647c918463202cbe607bb95557a4f7fd237069124333c54da5b2bbb76b

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
