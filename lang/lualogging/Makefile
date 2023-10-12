include $(TOPDIR)/rules.mk

PKG_NAME:=lualogging
PKG_VERSION:=1.8.2
PKG_RELEASE:=1
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYRIGHT

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/lunarmodules/lualogging/archive/refs/tags/v${PKG_VERSION}.tar.gz?
PKG_HASH:=30655889db14104f1509d20ba423a43ea8ce85f4289acdcf6b62477159482c60

PKG_BUILD_DEPENDS:=lua/host luarocks/host

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/lualogging
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Simple API to use logging features in Lua
  URL:=https://github.com/lunarmodules/lualogging
  DEPENDS:= +lua +luajit +luasocket
endef

define Package/lualogging/description
  LuaLogging provides a simple API to use logging features in Lua. Its design was based on log4j.
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
	luarocks make --pack-binary-rock rockspecs/lualogging-${PKG_VERSION}-1.rockspec \
		LUA_LIBDIR=$(STAGING_DIR)/usr/lib/lua \
		YAML_DIR=$(STAGING_DIR)/usr \
		LUA_INCDIR=$(STAGING_DIR)/usr/include \
		LUA_PKGNAME=lua5.1 \
		CFLAGS="$(TARGET_CFLAGS) $(FPIC)" \
		LDFLAGS="$(TARGET_LDFLAGS)" \
		CC="$(TARGET_CC)" LD="$(TARGET_CC)"
endef

define Package/lualogging/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/logging
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/src/logging/* $(1)/usr/lib/lua/logging/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/src/logging.lua $(1)/usr/lib/lua/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,lualogging))
