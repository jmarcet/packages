#
# Copyright (C) 2020 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-dockerpty
PKG_VERSION:=0.4.1
PKG_RELEASE:=1

PYPI_NAME:=dockerpty
PKG_HASH:=69a9d69d573a0daa31bcd1c0774eeed5c15c295fe719c61aca550ed1393156ce

PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE.txt
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

PYTHON3_PKG_SETUP_ARGS:=

define Package/python3-dockerpty
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python library to use the pseudo-tty of a docker container
  URL:=https://github.com/d11wtq/dockerpty
  DEPENDS:=+PACKAGE_python3-dockerpty:python3 +PACKAGE_python3-dockerpty:python3-docker
  VARIANT:=python3
endef

define Package/python3-dockerpty/description
Python library to use the pseudo-tty of a docker container
endef

$(eval $(call Py3Package,python3-dockerpty))
$(eval $(call BuildPackage,python3-dockerpty))
$(eval $(call BuildPackage,python3-dockerpty-src))
