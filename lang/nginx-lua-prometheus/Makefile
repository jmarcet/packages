include $(TOPDIR)/rules.mk

PKG_NAME:=nginx-lua-prometheus
PKG_VERSION:=0.20221218
PKG_RELEASE:=1
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/knyar/nginx-lua-prometheus/archive/refs/tags
PKG_HASH:=ab23987fd592291b3dea490d1faf0a74e3b43f6ea2e5d7355de55b426ee7d990

HOST_BUILD_DEPENDS:=lua/host luarocks/host

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/nginx-lua-prometheus
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Prometheus metric library for Nginx
  URL:=https://github.com/knyar/nginx-lua-prometheus
  DEPENDS:= +lua
endef

define Package/ngina-lua-prometheus/description
  Lua library that can be used with Nginx to keep track of metrics and expose them to be pulled by Prometheus.
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
	luarocks make --pack-binary-rock nginx-lua-prometheus-${PKG_VERSION}-1.rockspec \
		LUA_LIBDIR=$(STAGING_DIR)/usr/lib/lua \
		YAML_DIR=$(STAGING_DIR)/usr \
		LUA_INCDIR=$(STAGING_DIR)/usr/include \
		LUA_PKGNAME=lua5.1 \
		CFLAGS="$(TARGET_CFLAGS) $(FPIC)" \
		LDFLAGS="$(TARGET_LDFLAGS)" \
		CC="$(TARGET_CC)" LD="$(TARGET_CC)"
endef


define Package/nginx-lua-prometheus/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/prometheus{,_keys,_resty_counter}.lua $(1)/usr/lib/lua/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,nginx-lua-prometheus))
