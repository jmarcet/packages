include $(TOPDIR)/rules.mk

PKG_NAME:=buildx
PKG_VERSION:=0.36.1
PKG_RELEASE:=1
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=$(PKG_NAME)-v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/docker/buildx/tar.gz/v${PKG_VERSION}?
PKG_HASH:=8959987919445ab61564f50decde4dae810137063d84e2d3c969c9a4a68ecdeb

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/docker/buildx
GO_PKG_BUILD_PKG:=github.com/docker/buildx/cmd/buildx
GO_PKG_LDFLAGS_X:=github.com/docker/buildx/version.Version=v$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include ../../lang/golang/golang-package.mk

define Package/docker-buildx
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Docker Buildx
  URL:=https://github.com/docker/buildx
  DEPENDS:=$(GO_ARCH_DEPENDS) +docker
endef

define Package/docker-buildx/description
  Extended build capabilities with BuildKit for Docker
endef

define Package/docker-buildx/install
	$(INSTALL_DIR) $(1)/usr/lib/docker/cli-plugins/
	$(INSTALL_BIN) $(GO_PKG_BUILD_BIN_DIR)/buildx $(1)/usr/lib/docker/cli-plugins/docker-buildx
	$(INSTALL_DIR) $(1)/usr/bin/
	$(LN) ../lib/docker/cli-plugins/docker-buildx $(1)/usr/bin/docker-buildx
endef

$(eval $(call GoBinPackage,docker-buildx))
$(eval $(call BuildPackage,docker-buildx))
