#
# Copyright (C) 2020 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=docker-compose
PKG_VERSION:=1.25.4
PKG_RELEASE:=1

PYPI_NAME:=docker-compose
PKG_HASH:=fabae2bee4abfa7bdd09125b6bbdcdda81f946c7b16e3ccc6bb2d821ef6488f3

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python3-package.mk

PYTHON3_PKG_SETUP_ARGS:=

define Package/docker-compose
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Docker Compose
  URL:=https://github.com/docker/compose
  DEPENDS+= +docker-ce \
      +PACKAGE_docker-compose:python3 \
      +PACKAGE_docker-compose:python3-cached-property \
      +PACKAGE_docker-compose:python3-certifi \
      +PACKAGE_docker-compose:python3-chardet \
      +PACKAGE_docker-compose:python3-colorama \
      +PACKAGE_docker-compose:python3-docopt \
      +PACKAGE_docker-compose:python3-docker \
      +PACKAGE_docker-compose:python3-dockerpty \
      +PACKAGE_docker-compose:python3-idna \
      +PACKAGE_docker-compose:python3-jsonschema \
      +PACKAGE_docker-compose:python3-paramiko \
      +PACKAGE_docker-compose:python3-pip \
      +PACKAGE_docker-compose:python3-pkg-resources \
      +PACKAGE_docker-compose:python3-pyrsistent \
      +PACKAGE_docker-compose:python3-requests \
      +PACKAGE_docker-compose:python3-setuptools \
      +PACKAGE_docker-compose:python3-six \
      +PACKAGE_docker-compose:python3-texttable \
      +PACKAGE_docker-compose:python3-websocket-client \
      +PACKAGE_docker-compose:python3-yaml
  VARIANT:=python3
endef

define Package/docker-compose/description
  Multi-container orchestration for Docker
endef

$(eval $(call Py3Package,docker-compose))
$(eval $(call BuildPackage,docker-compose))
$(eval $(call BuildPackage,docker-compose-src))
