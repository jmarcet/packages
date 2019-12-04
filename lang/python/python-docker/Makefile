#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-docker
PKG_VERSION:=4.1.0
PKG_RELEASE:=1

PYPI_NAME:=docker
PKG_HASH:=6e06c5e70ba4fad73e35f00c55a895a448398f3ada7faae072e2bb01348bafc1

PKG_LICENSE:=Apache
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-docker/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=A Python library for the Docker Engine API
  URL:=https://github.com/docker/docker-py
endef

define Package/python-docker
$(call Package/python-docker/Default)
  DEPENDS:=+PACKAGE_python-docker:python-light
  VARIANT:=python
endef

define Package/python3-docker
$(call Package/python-docker/Default)
  DEPENDS:=+PACKAGE_python3-docker:python3-light
  VARIANT:=python3
endef

define Package/python-docker/description
A Python library for the Docker Engine API
endef

define Package/python3-docker/description
$(call Package/python-docker/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-docker))
$(eval $(call BuildPackage,python-docker))
$(eval $(call BuildPackage,python-docker-src))

$(eval $(call Py3Package,python3-docker))
$(eval $(call BuildPackage,python3-docker))
$(eval $(call BuildPackage,python3-docker-src))
