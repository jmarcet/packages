include $(TOPDIR)/rules.mk

PKG_NAME:=apk
PKG_VERSION:=2.14.0
PKG_RELEASE:=1

PKG_SOURCE:=apk.static
PKG_SOURCE_URL:=https://gitlab.alpinelinux.org/api/v4/projects/5/packages/generic//v${PKG_VERSION}/${ARCH}
PKG_HASH:=1c65115a425d049590bec7c729c7fd88357fbb090a6fc8c31d834d7b0bc7d6f2
# https://gitlab.alpinelinux.org/alpine/apk-tools/-/releases

PKG_MAINTAINER:=Paul Spooren <mail@aparcar.org>
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Build/Prepare
endef

define Build/Compile
endef

define Build/Install
endef

define Package/apk
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=apk package manager
  DEPENDS:=@!arc
  URL:=$(PKG_SOURCE_URL)
endef

define Package/alpine-keys
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Alpine apk public signing keys
  DEPENDS:=apk
endef

define Package/alpine-repositories
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Official Alpine repositories
  DEPENDS:=apk
endef

define Package/apk/install
	$(INSTALL_DIR) $(1)/lib/apk/db

	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(DL_DIR)/apk.static $(1)/sbin/apk

	$(INSTALL_DIR) $(1)/etc/apk/
	echo $(ARCH) > $(1)/etc/apk/arch
	touch $(1)/etc/apk/world
endef

define Package/alpine-keys/install
	$(INSTALL_DIR) $(1)/etc/apk/keys
	$(INSTALL_DATA) ./files/alpine-keys/* $(1)/etc/apk/keys
endef

define Package/alpine-repositories/install
	$(INSTALL_DIR) $(1)/etc/apk/keys
	$(INSTALL_DATA) ./files/alpine-repositories $(1)/etc/apk/repositories
endef

$(eval $(call BuildPackage,apk))
$(eval $(call BuildPackage,alpine-keys))
$(eval $(call BuildPackage,alpine-repositories))
