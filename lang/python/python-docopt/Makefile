#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-docopt
PKG_VERSION:=0.6.2
PKG_RELEASE:=1

PYPI_NAME:=docopt
PKG_HASH:=49b3a825280bd66b3aa83585ef59c4a8c82f2c8a522dbe754a8bc8d08c85c491

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

PYTHON_PKG_SETUP_ARGS:=
PYTHON3_PKG_SETUP_ARGS:=

define Package/python-docopt/Default
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Pythonic argument parser, that will make you smile
  URL:=http://docopt.org/
endef

define Package/python-docopt
$(call Package/python-docopt/Default)
  DEPENDS:=+PACKAGE_python-docopt:python-light
  VARIANT:=python
endef

define Package/python3-docopt
$(call Package/python-docopt/Default)
  DEPENDS:=+PACKAGE_python3-docopt:python3-light
  VARIANT:=python3
endef

define Package/python-docopt/description
Pythonic argument parser, that will make you smile
endef

define Package/python3-docopt/description
$(call Package/python-docopt/description)
.
(Variant for Python3)
endef

$(eval $(call PyPackage,python-docopt))
$(eval $(call BuildPackage,python-docopt))
$(eval $(call BuildPackage,python-docopt-src))

$(eval $(call Py3Package,python3-docopt))
$(eval $(call BuildPackage,python3-docopt))
$(eval $(call BuildPackage,python3-docopt-src))
