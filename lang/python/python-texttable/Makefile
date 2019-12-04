#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-texttable
PKG_VERSION:=1.6.2
PKG_RELEASE:=1

PYPI_NAME:=texttable
PKG_HASH:=eff3703781fbc7750125f50e10f001195174f13825a92a45e9403037d539b4f4

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-texttable/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=module for creating simple ASCII tables
  URL:=https://github.com/foutaise/texttable/
endef

define Package/python-texttable
$(call Package/python-texttable/Default)
  DEPENDS:=+PACKAGE_python-texttable:python-light
  VARIANT:=python
endef

define Package/python3-texttable
$(call Package/python-texttable/Default)
  DEPENDS:=+PACKAGE_python3-texttable:python3-light
  VARIANT:=python3
endef

define Package/python-texttable/description
module for creating simple ASCII tables
endef

define Package/python3-texttable/description
$(call Package/python-texttable/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-texttable))
$(eval $(call BuildPackage,python-texttable))
$(eval $(call BuildPackage,python-texttable-src))

$(eval $(call Py3Package,python3-texttable))
$(eval $(call BuildPackage,python3-texttable))
$(eval $(call BuildPackage,python3-texttable-src))
