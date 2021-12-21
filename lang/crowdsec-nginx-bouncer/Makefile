include $(TOPDIR)/rules.mk

PKG_NAME:=crowdsec-nginx-bouncer
PKG_VERSION:=v0.0.8
PKG_RELEASE:=1
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=${PKG_NAME}.tgz
PKG_SOURCE_URL:=https://github.com/crowdsecurity/cs-nginx-bouncer/releases/download/v${PKG_VERSION}/
PKG_HASH:=ec6352ff8cd122e826919df7cfa9a28b3490db2e67da24d2c8bd21ec30884578

include $(INCLUDE_DIR)/package.mk

define Package/crowdsec-nginx-bouncer
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=CrowdSec NGINX Bouncer
  URL:=https://github.com/crowdsecurity/cs-nginx-bouncer
  DEPENDS:= +lua +lua-cs-bouncer
endef

define Package/crowdsec-nginx-bouncer/description
  A lua bouncer for nginx
endef

define Build/Compile
endef

define Package/crowdsec-nginx-bouncer/install
	$(INSTALL_DIR) $(1)/etc/crowdsec/bouncers
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/config/crowdsec.conf $(1)/etc/crowdsec/bouncers/crowdsec-nginx-bouncer.conf
	$(INSTALL_DIR) $(1)/etc/nginx/conf.d
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/nginx/crowdsec_nginx.conf $(1)/etc/nginx/conf.d/
	$(INSTALL_DIR) $(1)/usr/lib/lua/crowdsec/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/nginx/access.lua $(1)/usr/lib/lua/crowdsec/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,crowdsec-nginx-bouncer))
