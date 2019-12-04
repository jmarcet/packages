#
# Copyright (C) 2008-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-yaml-3
PKG_VERSION:=3.13
PKG_RELEASE:=1

PYPI_NAME:=PyYAML
PKG_HASH:=3ef3092145e9b70e3ddd2c7ad59bdd0252a94dfe3949721633e41344de00a6bf

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_CPE_ID:=cpe:/a:pyyaml_project:pyyaml

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-yaml-3/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=YAML parser and emitter for Python v3
  URL:=https://github.com/yaml/pyyaml
  DEPENDS:=+libyaml
endef

define Package/python-yaml-3
$(call Package/python-yaml-3/Default)
  DEPENDS+= \
	+PACKAGE_python-yaml-3:python-light \
	+PACKAGE_python-yaml-3:python-codecs
  VARIANT:=python
endef

define Package/python3-yaml-3
$(call Package/python-yaml-3/Default)
  DEPENDS+=+PACKAGE_python3-yaml-3:python3-light
  VARIANT:=python3
endef

define Package/python-yaml-3/description
  PyYAML is a YAML parser and emitter for the Python programming language.
endef

define Package/python3-yaml-3/description
$(call Package/python-yaml-3/description)
.
(Variant for Python3)
endef

PYTHON_PKG_SETUP_GLOBAL_ARGS:=--with-libyaml
PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_GLOBAL_ARGS:=--with-libyaml
PYTHON3_PKG_SETUP_ARGS:=

$(eval $(call PyPackage,python-yaml-3))
$(eval $(call BuildPackage,python-yaml-3))
$(eval $(call BuildPackage,python-yaml-3-src))

$(eval $(call Py3Package,python3-yaml-3))
$(eval $(call BuildPackage,python3-yaml-3))
$(eval $(call BuildPackage,python3-yaml-3-src))
