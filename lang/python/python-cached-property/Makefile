#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-cached-property
PKG_VERSION:=1.5.1
PKG_RELEASE:=1

PYPI_NAME:=cached-property
PKG_HASH:=9217a59f14a5682da7c4b8829deadbfc194ac22e9908ccf7c8820234e80a1504

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-cached-property/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=A decorator for caching properties in classes
  URL:=https://github.com/pydanny/cached-property
endef

define Package/python-cached-property
$(call Package/python-cached-property/Default)
  DEPENDS:=+PACKAGE_python-cached-property:python
  VARIANT:=python
endef

define Package/python3-cached-property
$(call Package/python-cached-property/Default)
  DEPENDS:=+PACKAGE_python3-cached-property:python3
  VARIANT:=python3
endef

define Package/python-cached-property/description
A decorator for caching properties in classes.
endef

define Package/python3-cached-property/description
$(call Package/python-cached-property/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-cached-property))
$(eval $(call BuildPackage,python-cached-property))
$(eval $(call BuildPackage,python-cached-property-src))

$(eval $(call Py3Package,python3-cached-property))
$(eval $(call BuildPackage,python3-cached-property))
$(eval $(call BuildPackage,python3-cached-property-src))
