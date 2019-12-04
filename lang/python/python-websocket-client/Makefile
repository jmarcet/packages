#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-websocket-client
PKG_VERSION:=0.56.0
PKG_RELEASE:=1

PYPI_NAME:=websocket_client
PKG_HASH:=1fd5520878b68b84b5748bb30e592b10d0a91529d5383f74f4964e72b297fd3a

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-websocket-client/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=WebSocket client for Python. hybi13 is supported
  URL:=https://github.com/websocket-client/websocket-client.git
endef

define Package/python-websocket-client
$(call Package/python-websocket-client/Default)
  DEPENDS:=+PACKAGE_python-websocket-client:python-light
  VARIANT:=python
endef

define Package/python3-websocket-client
$(call Package/python-websocket-client/Default)
  DEPENDS:=+PACKAGE_python3-websocket-client:python3-light
  VARIANT:=python3
endef

define Package/python-websocket-client/description
WebSocket client for Python. hybi13 is supported
endef

define Package/python3-websocket-client/description
$(call Package/python-websocket-client/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-websocket-client))
$(eval $(call BuildPackage,python-websocket-client))
$(eval $(call BuildPackage,python-websocket-client-src))

$(eval $(call Py3Package,python3-websocket-client))
$(eval $(call BuildPackage,python3-websocket-client))
$(eval $(call BuildPackage,python3-websocket-client-src))
