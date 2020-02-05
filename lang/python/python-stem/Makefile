#
# Copyright (C) 2020 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-stem
PKG_VERSION:=1.8.0
PKG_RELEASE:=1

PYPI_NAME:=stem
PKG_HASH:=a0b48ea6224e95f22aa34c0bc3415f0eb4667ddeae3dfb5e32a6920c185568c2

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

PYTHON3_PKG_SETUP_ARGS:=

define Package/python3-stem
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python controller library that allows applications to interact with Tor
  URL:=https://stem.torproject.org/
  DEPENDS:=+PACKAGE_python3-stem:python3-light
  VARIANT:=python3
endef

define Package/python3-stem/description
  Python controller library that allows applications to interact with Tor
endef

$(eval $(call Py3Package,python3-stem))
$(eval $(call BuildPackage,python3-stem))
$(eval $(call BuildPackage,python3-stem-src))
