#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-jsonschema
PKG_VERSION:=3.2.0
PKG_RELEASE:=1

PYPI_NAME:=jsonschema
PKG_HASH:=c8a85b28d377cc7737e46e2d9f2b4f44ee3c0e1deac6bf46ddefc7187d30797a

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-jsonschema/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=An implementation of JSON Schema validation for Python
  URL:=https://github.com/Julian/jsonschema
endef

define Package/python-jsonschema
$(call Package/python-jsonschema/Default)
  DEPENDS:=+PACKAGE_python-jsonschema:python-light
  VARIANT:=python
endef

define Package/python3-jsonschema
$(call Package/python-jsonschema/Default)
  DEPENDS:=+PACKAGE_python3-jsonschema:python3-light
  VARIANT:=python3
endef

define Package/python-jsonschema/description
An implementation of JSON Schema validation for Python
endef

define Package/python3-jsonschema/description
$(call Package/python-jsonschema/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-jsonschema))
$(eval $(call BuildPackage,python-jsonschema))
$(eval $(call BuildPackage,python-jsonschema-src))

$(eval $(call Py3Package,python3-jsonschema))
$(eval $(call BuildPackage,python3-jsonschema))
$(eval $(call BuildPackage,python3-jsonschema-src))
