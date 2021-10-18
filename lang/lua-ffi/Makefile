include $(TOPDIR)/rules.mk

PKG_NAME:=lua-ffi
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/zhaozg/lua-ffi
PKG_SOURCE_DATE:=2021-06-14
PKG_SOURCE_VERSION=60cf05da576829586136a4e8f8f4f820a6b990e7
PKG_MIRROR_HASH:=34c984682d11cb7271c696d395aa17274b40f927b862591e350cc8a04d1580c2

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=lua/host luarocks/host

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/lua-ffi
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Lua library for calling C function and manipulating C types from lua
  URL:=https://github.com/zhaozg/lua-ffi
  DEPENDS:= +lua +luajit
endef

define Package/lua-ffi/description
  Lua library for calling C function and manipulating C types from lua. It is designed to be interface compatible with the FFI library in LuaJIT
endef

TARGET_CFLAGS += \
	-I$(STAGING_DIR)/usr/include

# Note: the duplicate environment exports are not a typo!
# First is for luarocks, then the second is for the compilation
# invoked by luarocks
# (Same setup as luaposix)
define Build/Compile
	cd $(PKG_BUILD_DIR) && \
	LUA_LIBDIR=$(STAGING_DIR)/usr/lib/lua \
	LUA_PKGNAME=lua5.1 \
	CFLAGS="$(TARGET_CFLAGS) $(FPIC)" \
	LDFLAGS="$(TARGET_LDFLAGS)" \
	CC="$(TARGET_CC)" LD="$(TARGET_CC)" \
	luarocks make \
		LUA_LIBDIR=$(STAGING_DIR)/usr/lib/lua \
		YAML_DIR=$(STAGING_DIR)/usr \
		LUA_INCDIR=$(STAGING_DIR)/usr/include \
		LUA_PKGNAME=lua5.1 \
		CFLAGS="$(TARGET_CFLAGS) $(FPIC)" \
		LDFLAGS="$(TARGET_LDFLAGS)" \
		CC="$(TARGET_CC)" LD="$(TARGET_CC)"
endef

define Package/lua-ffi/install
	$(INSTALL_DIR) $(1)/usr/lib/lua
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ffi.so $(1)/usr/lib/lua/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,lua-ffi))
