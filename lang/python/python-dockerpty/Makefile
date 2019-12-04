#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
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

PKG_LICENSE:=Apache
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-dockerpty/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python library to use the pseudo-tty of a docker container
  URL:=https://github.com/d11wtq/dockerpty
endef

define Package/python-dockerpty
$(call Package/python-dockerpty/Default)
  DEPENDS:=+PACKAGE_python-dockerpty:python +PACKAGE_python-dockerpty:python-docker
  VARIANT:=python
endef

define Package/python3-dockerpty
$(call Package/python-dockerpty/Default)
  DEPENDS:=+PACKAGE_python3-dockerpty:python3 +PACKAGE_python3-dockerpty:python3-docker
  VARIANT:=python3
endef

define Package/python-dockerpty/description
Python library to use the pseudo-tty of a docker container
endef

define Package/python3-dockerpty/description
$(call Package/python-dockerpty/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-dockerpty))
$(eval $(call BuildPackage,python-dockerpty))
$(eval $(call BuildPackage,python-dockerpty-src))

$(eval $(call Py3Package,python3-dockerpty))
$(eval $(call BuildPackage,python3-dockerpty))
$(eval $(call BuildPackage,python3-dockerpty-src))
