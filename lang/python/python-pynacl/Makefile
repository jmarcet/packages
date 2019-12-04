#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-pynacl
PKG_VERSION:=1.3.0
PKG_RELEASE:=1

PYPI_NAME:=PyNaCl
PKG_HASH:=0c6100edd16fefd1557da078c7a31e7b7d7a52ce39fdca2bec29d4f7b6e7600c

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=Apache

PKG_BUILD_DEPENDS:=libffi/host

HOST_PYTHON_PACKAGE_BUILD_DEPENDS:="cffi>=1.8,!=1.11.3"
HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:="cffi>=1.8,!=1.11.3"

CONFIG_PACKAGE_python-packages-envs+="SODIUM_INSTALL=system"
CONFIG_PACKAGE_python3-packages-envs+="SODIUM_INSTALL=system"

include ../pypi.mk
include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-pynacl/Default
  CATEGORY:=Languages
  SECTION:=lang
  SUBMENU:=Python
  TITLE:=Python binding to the Networking and Cryptography (NaCl) library
  URL:=https://github.com/pyca/pynacl/
  DEPENDS:=+libsodium
endef

define Package/python-pynacl
$(call Package/python-pynacl/Default)
  DEPENDS+= \
      +PACKAGE_python-pynacl:python \
      +PACKAGE_python-pynacl:python-cffi \
      +PACKAGE_python-pynacl:python-distutils \
      +PACKAGE_python-pynacl:python-setuptools \
      +PACKAGE_python-pynacl:python-six
  VARIANT:=python
endef

define Package/python-pynacl/description
  PyNaCl is a Python binding to libsodium, which is a fork of the Networking and Cryptography library.
endef

define Package/python3-pynacl
$(call Package/python-pynacl/Default)
  DEPENDS+= \
      +PACKAGE_python3-pynacl:python3 \
      +PACKAGE_python3-pynacl:python3-cffi \
      +PACKAGE_python3-pynacl:python3-distutils \
      +PACKAGE_python3-pynacl:python3-setuptools \
      +PACKAGE_python3-pynacl:python3-six
  VARIANT:=python3
endef

define Package/python3-pynacl/description
$(call Package/python-pynacl/description)
.
(Variant for Python3)
endef

#PYTHON_PKG_SETUP_ARGS:=
#PYTHON3_PKG_SETUP_ARGS:=

$(eval $(call PyPackage,python-pynacl))
$(eval $(call BuildPackage,python-pynacl))
$(eval $(call BuildPackage,python-pynacl-src))

$(eval $(call Py3Package,python3-pynacl))
$(eval $(call BuildPackage,python3-pynacl))
$(eval $(call BuildPackage,python3-pynacl-src))
