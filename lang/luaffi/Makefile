include $(TOPDIR)/rules.mk

PKG_NAME:=luaffi
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/jmckaskill/luaffi
PKG_SOURCE_DATE:=2013-11-08
PKG_SOURCE_VERSION=abc638c9341025580099dcf77795c4b320ba0e63
PKG_MIRROR_HASH:=947afe2f7f0e49f1b3f1bc8ef3ed95f413e17faa8c27c7b3339429baabdd66a6

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=README.md

PKG_BUILD_DEPENDS:=lua/host

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/luaffi
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Library for calling C function and manipulating C types from lua
  URL:=https://github.com/jmckaskill/luaffi
  DEPENDS:= +lua
endef

define Package/luaffi/description
  Library for calling C function and manipulating C types from lua. Designed to be interface compatible with the FFI library in luajit.
endef

define Package/luaffi/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/ffi.so $(1)/usr/lib/lua/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,luaffi))
