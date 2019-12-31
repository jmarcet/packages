include $(TOPDIR)/rules.mk

PKG_NAME:=ctop
PKG_RELEASE:=1
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_URL:=https://github.com/bcicen/ctop
PKG_MIRROR_HASH:=f2b5b50ab8bf67b83f864f85b732bfbeaafb3dbb6c561a05c218418535dafd69
PKG_SOURCE_VERSION:=9dd12103fc9ef78a80f90b7142b2140c33739fee
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2019-12-30

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1

GO_PKG:=github.com/bcicen/ctop

include $(INCLUDE_DIR)/package.mk
include ../../lang/golang/golang-package.mk

define Package/ctop
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Top-like interface for container metrics
  URL:=https://ctop.sh/
  DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/ctop/description
Top-like interface for container metrics
endef

MAKE_PATH:=$(GO_PKG_WORK_DIR_NAME)/build/src/$(GO_PKG)
MAKE_VARS += \
	GOPATH=$(GO_PKG_BUILD_DIR) \
	GOCACHE=$(GO_PKG_CACHE_DIR) \
	GOTMPDIR=$(GO_PKG_TMP_DIR) \
	GOROOT_FINAL=$(GO_TARGET_ROOT) \
	CC=$(TARGET_CC) \
	CXX=$(TARGET_CXX) \
	$(call GoPackage/Environment)
MAKE_FLAGS += \
	COMMIT=$(PKG_SOURCE_VERSION)

define Package/ctop/install
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(GO_PKG_BUILD_DIR)/bin/ctop $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ctop))
