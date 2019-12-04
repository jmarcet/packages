#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-paramiko
PKG_VERSION:=2.7.0
PKG_RELEASE:=1

PYPI_NAME:=paramiko
PKG_HASH:=fba9c46340e3d690ad5a9d0dbf06677cd91425de3afa7e9c0c187298ee4ddd0d

PKG_LICENSE:=LGPL
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-paramiko/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=SSH2 protocol library
  URL:=https://github.com/paramiko/paramiko/
endef

define Package/python-paramiko
$(call Package/python-paramiko/Default)
  DEPENDS:=+PACKAGE_python-paramiko:python-light
  VARIANT:=python
endef

define Package/python3-paramiko
$(call Package/python-paramiko/Default)
  DEPENDS:=+PACKAGE_python3-paramiko:python3-light
  VARIANT:=python3
endef

define Package/python-paramiko/description
SSH2 protocol library
endef

define Package/python3-paramiko/description
$(call Package/python-paramiko/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-paramiko))
$(eval $(call BuildPackage,python-paramiko))
$(eval $(call BuildPackage,python-paramiko-src))

$(eval $(call Py3Package,python3-paramiko))
$(eval $(call BuildPackage,python3-paramiko))
$(eval $(call BuildPackage,python3-paramiko-src))
