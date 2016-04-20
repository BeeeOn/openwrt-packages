#
# Copyright (c) 2016, Brno University of Technology
#
# Licensing conditions are outlined in /LICENSE
#

include $(TOPDIR)/rules.mk

PKG_NAME:=beeeon-gateway
PKG_VERSION:=1.6.1
PKG_RELEASE:=1
INIT_SCRIPT_NAME:=$(PKG_NAME)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=+libmosquittopp +poco
PKG_SOURCE_URL:=https://github.com/BeeeOn/gateway-app.git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_SOURCE_SUBDIR)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DCMAKE_INSTALL_PREFIX=/
CMAKE_OPTIONS += -DPOCO_NO_FLOAT=ON
CMAKE_OPTIONS += -DADAAPP_NO_SYSTEMD=ON

define Package/$(PKG_NAME)
	TITLE:=$(PKG_NAME)
	DEPENDS:=+poco +libmosquittopp
	URL:=http://beeeon.org
	MAINTAINER:=Matej Postolka <xposto02@stud.fit.vutbr.cz>
endef

define Package/$(PKG_NAME)/description
 Main application for BeeeOn Gateway. More information and other resources are published on our wiki page at beeeon.org
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)
	$(CP) -r $(PKG_INSTALL_DIR)/* $(1)

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/$(INIT_SCRIPT_NAME) $(1)/etc/init.d/$(INIT_SCRIPT_NAME)
endef

define Package/$(PKG_NAME)/postinst
#!/bin/sh
if [ -z "$${IPKG_INSTROOT}" ]; then
  echo "Enabling and starting $(PKG_NAME) service"
  /etc/init.d/$(INIT_SCRIPT_NAME) enable
  /etc/init.d/$(INIT_SCRIPT_NAME) start
fi
exit 0
endef

define Package/$(PKG_NAME)/prerm
#!/bin/sh
if [ -z "$${IPKG_INSTROOT}" ]; then
  echo "Disabling and stopping $(PKG_NAME) service"
  /etc/init.d/$(INIT_SCRIPT_NAME) disable
  /etc/init.d/$(INIT_SCRIPT_NAME) stop
fi
exit 0
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
