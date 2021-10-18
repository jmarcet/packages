include $(TOPDIR)/rules.mk

PKG_NAME:=cs-nginx-bouncer
PKG_VERSION:=0.0.7
PKG_RELEASE:=1
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/crowdsecurity/cs-nginx-bouncer/archive/refs/tags
PKG_HASH:=489a269c65ebf477810826f6115a5fd63a3c14b72d5bcc8b4854b24f8c38b329

include $(INCLUDE_DIR)/package.mk

define Package/cs-nginx-bouncer
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=CrowdSec NGINX Bouncer
  URL:=https://github.com/crowdsecurity/cs-nginx-bouncer
  DEPENDS:= +lua +lua-cs-bouncer
endef

define Package/cs-nginx-bouncer/description
  A lua bouncer for nginx
endef

define Package/cs-nginx-bouncer/install
	$(INSTALL_DIR) $(1)/etc/crowdsec/bouncers
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/config/crowdsec.conf $(1)/etc/crowdsec/bouncers/crowdsec-nginx-bouncer.conf
	$(INSTALL_DIR) $(1)/etc/nginx/conf.d
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/nginx/crowdsec_nginx.conf $(1)/etc/nginx/conf.d/
	$(INSTALL_DIR) $(1)/usr/lib/lua/crowdsec/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/nginx/access.lua $(1)/usr/lib/lua/crowdsec/
endef

$(eval $(call HostBuild))
$(eval $(call BuildPackage,cs-nginx-bouncer))
