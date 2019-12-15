# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nyx
PKG_VERSION:=2.1.0
PKG_RELEASE:=1

PYPI_NAME:=nyx
PKG_HASH:=88521488d1c9052e457b9e66498a4acfaaa3adf3adc5a199892632f129a5390b

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

include ../../lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../../lang/python/python3-package.mk

define Package/nyx
  SECTION:=admin
  CATEGORY:=Administration
  URL:=https://nyx.torproject.org/
  TITLE:=nyx
  DEPENDS:=+python3-light +python3-stem
  VARIANT:=python3
endef

define Package/nyx/description
  Terminal status monitor for Tor
endef

$(eval $(call Py3Package,nyx))
$(eval $(call BuildPackage,nyx))
$(eval $(call BuildPackage,nyx-src))
