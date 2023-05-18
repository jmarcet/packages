include $(TOPDIR)/rules.mk

PKG_NAME:=luajit
PKG_RELEASE:=8

ifneq ($(BUILD_VARIANT),openresty)
  PKG_VERSION:=2.1.0-beta3
  PKG_SOURCE:=LuaJIT-$(PKG_VERSION).tar.gz
  PKG_SOURCE_URL:=https://luajit.org/download
  PKG_HASH:=1ad2e34b111c802f9d0cdf019e986909123237a28c746b21295b63c9e785d9c3
  PKG_BUILD_DIR:=$(BUILD_DIR)/LuaJIT-$(PKG_VERSION)
else
  PKG_VERSION:=2.1-20230410
  PKG_SOURCE:=luajit2-$(PKG_VERSION).tar.gz
  PKG_SOURCE_URL:=https://codeload.github.com/openresty/luajit2/tar.gz/v$(PKG_VERSION)?
  PKG_HASH:=77bbcbb24c3c78f51560017288f3118d995fe71240aa379f5818ff6b166712ff
  PKG_BUILD_DIR:=$(BUILD_DIR)/luajit2-$(PKG_VERSION)
  PATCH_DIR:=./patches-openresty
endif

PKG_MAINTAINER:=Morteza Milani <milani@pichak.co>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYRIGHT

PKG_BUILD_FLAGS:=no-mips16

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk

define Package/luajit
 SECTION:=lang
 CATEGORY:=Languages
 SUBMENU:=Lua
 TITLE:=LuaJIT
 URL:=https://www.luajit.org
 DEPENDS:=@(i386||x86_64||arm||armeb||aarch64||powerpc||mips||mipsel||mips64)
endef

define Package/luajit/description
 LuaJIT is a Just-In-Time (JIT) compiler for the Lua programming language. *** Requires GCC Multilib on host system to build! ***
endef

define Package/luajit2
 $(Package/luajit)
 TITLE += from OpenResty
 VARIANT:=openresty
 PROVIDES:=luajit
endef

Package/luajit2/description = $(Package/luajit/description) \
 OpenResty's maintained branch of LuaJIT

ifeq ($(HOST_ARCH),$(filter $(HOST_ARCH), x86_64 mips64))
  ifeq ($(CONFIG_ARCH_64BIT),)
    HOST_BITS := -m32
  endif
endif

define Build/Compile
	$(MAKE) $(PKG_JOBS) -C $(PKG_BUILD_DIR) \
		HOST_CC="$(HOSTCC) $(HOST_CFLAGS) $(HOST_BITS)" \
		CROSS="$(TARGET_CROSS)" \
		DPREFIX=$(PKG_INSTALL_DIR)/usr \
		PREFIX=/usr \
		TARGET_SYS=Linux \
		TARGET_CFLAGS="$(TARGET_CFLAGS)" \
		BUILDMODE=dynamic
	rm -rf $(PKG_INSTALL_DIR)
	mkdir -p $(PKG_INSTALL_DIR)
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DPREFIX=$(PKG_INSTALL_DIR)/usr \
		PREFIX=/usr \
		TARGET_SYS=Linux \
		install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/luajit-2.1
	$(CP) $(PKG_INSTALL_DIR)/usr/include/luajit-2.1/*.{h,hpp} $(1)/usr/include/luajit-2.1
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/luajit.pc $(1)/usr/lib/pkgconfig/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/luajit-* $(1)/usr/bin/$(PKG_NAME)
endef

define Package/luajit/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/luajit-* $(1)/usr/bin/$(PKG_NAME)
endef

Package/luajit2/install = $(Package/luajit/install)

define Host/Compile
	$(MAKE) $(HOST_JOBS) -C $(HOST_BUILD_DIR) \
		DPREFIX=$(STAGING_DIR_HOSTPKG) \
		TARGET_CFLAGS="$(HOST_CFLAGS)" \
		TARGET_LDFLAGS="$(HOST_LDFLAGS)"
endef

define Host/Install
	$(MAKE) $(HOST_JOBS) -C $(HOST_BUILD_DIR) \
		DPREFIX=$(STAGING_DIR_HOSTPKG) \
		install
	$(CP) $(STAGING_DIR_HOSTPKG)/bin/luajit-* $(STAGING_DIR_HOSTPKG)/bin/$(PKG_NAME)
endef

$(eval $(call HostBuild,luajit))
$(eval $(call HostBuild,luajit2))
$(eval $(call BuildPackage,luajit))
$(eval $(call BuildPackage,luajit2))
