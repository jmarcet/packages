include $(TOPDIR)/rules.mk

PKG_NAME:=lua-cs-bouncer
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/crowdsecurity/lua-cs-bouncer/
PKG_SOURCE_DATE:=2021-09-09
PKG_SOURCE_VERSION=3e8c308bce050fda6b1917e65248fa17e1772b77
PKG_MIRROR_HASH:=11c603b7e9dd6761478b58b49890b067dff0c27147bf3429e44b6e210b375534

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

HOST_BUILD_DEPENDS:=lua/host

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk

define Package/lua-cs-bouncer
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Lua Crowdsec Bouncer module
  URL:=https://github.com/crowdsecurity/lua-cs-bouncer
  DEPENDS:= +lua +luaffi +lualogging +luasec
endef

define Package/lua-cs-bouncer/description
  Lua module to allow ip (or not) from CrowdSec API
endef

define Build/Compile
endef

define Package/lua-cs-bouncer/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/crowdsec
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/lib/*.lua $(1)/usr/lib/lua/crowdsec/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/template.conf $(1)/usr/lib/lua/crowdsec/crowdsec.conf
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,lua-cs-bouncer))
