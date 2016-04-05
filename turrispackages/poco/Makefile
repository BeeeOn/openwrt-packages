#
# Copyright (C) 2007-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=poco
PKG_VERSION:=1.6.1-all
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pocoproject.org/releases/poco-1.6.1
PKG_MD5SUM:=96f1395e2e73c153220764abb5d51408

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DENABLE_DATA=OFF
CMAKE_OPTIONS += -DARCH_PPC=ON

define Package/poco
  NAME:=poco
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Poco C++ libraries
  URL:=http://www.pocoproject.org/
  DEPENDS:=+libstdcpp +libpthread +librt +libopenssl
endef

define Package/poco/description
  Modern, powerful open source C++ class libraries and frameworks for building
  network- and internet-based applications that run on desktop, server and
  embedded systems.
endef

define Package/poco/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libPoco*.so* $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) -r $(PKG_INSTALL_DIR)/usr/include/Poco $(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libPoco*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,poco))
