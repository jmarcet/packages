include $(TOPDIR)/rules.mk

PKG_NAME:=mbuffer
PKG_VERSION:=20210209
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=https://www.maier-komor.de/software/mbuffer
PKG_HASH:=e81f2788e2621f20f848181ef2cb19ac6d12328691437f301574b253fd899a0c

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/mbuffer
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Tool for buffering data streams
  URL:=https://www.maier-komor.de/mbuffer.html
  DEPENDS:=+libopenssl
endef

define Package/mbuffer/description
A tool for buffering data streams with a large set of unique features
endef

define Package/mbuffer/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mbuffer $(1)/usr/bin/
endef

$(eval $(call BuildPackage,mbuffer))
