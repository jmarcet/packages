#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-stem
PKG_SOURCE_DATE:=2019-12-10
PKG_SOURCE_VERSION:=947c0c115085120181fd8c456238249a2f13f344
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://git.torproject.org/stem.git
PKG_MIRROR_HASH:=b405b3ec358995b8d6fc1706db9b2706bb41e8a0dd22ad620eddf948f08a90ec
PKG_HASH:=skip

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-stem/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python controller library that allows applications to interact with Tor
  URL:=https://stem.torproject.org/
endef

define Package/python-stem
$(call Package/python-stem/Default)
  DEPENDS:=+PACKAGE_python-stem:python-light
  VARIANT:=python
endef

define Package/python3-stem
$(call Package/python-stem/Default)
  DEPENDS:=+PACKAGE_python3-stem:python3-light
  VARIANT:=python3
endef

define Package/python-stem/description
  Python controller library that allows applications to interact with Tor
endef

define Package/python3-stem/description
$(call Package/python-stem/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-stem))
$(eval $(call BuildPackage,python-stem))
$(eval $(call BuildPackage,python-stem-src))

$(eval $(call Py3Package,python3-stem))
$(eval $(call BuildPackage,python3-stem))
$(eval $(call BuildPackage,python3-stem-src))
