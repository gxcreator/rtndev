#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=asciinema
PKG_VERSION:=0.9.8
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pypi.python.org/packages/source/a/$(PKG_NAME)
PKG_MD5SUM:=ae8662d033af0e973d5864a247117e7f
PKG_BUILD_DEPENDS:=distribute/host

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/asciinema
	SECTION:=utils
	CATEGORY:=Utilities
	SUBMENU:=Terminal
	DEPENDS:=+distribute +python-requests +ncurses-bin
	TITLE:=A terminal sessions recorder
	URL:=http://asciinema.org/
	MAINTAINER:=Entware team, entware.wl500g.info
endef

define Package/asciinema/description
 asciinema lets you record your terminal sessions and share it with other geeks.
endef

define Package/asciinema/conffiles
/opt/etc/asciinema/config
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/opt --root=$(PKG_INSTALL_DIR))
endef

define Package/asciinema/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/bin/$(PKG_NAME) $(1)/opt/bin
	$(SED) '1s/#\!.*/#\!\/opt\/bin\/python/' $(1)/opt/bin/$(PKG_NAME)
endef

$(eval $(call BuildPackage,asciinema))
