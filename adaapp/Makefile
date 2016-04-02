#
# BeeeOn Project 2016
# Matej Postolka <xposto02@stud.fit.vutbr.cz>
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gateway-app
PKG_VERSION:=1.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=ssh://xposto02@ant-2.fit.vutbr.cz:/srv/git/iot/adaapp-new.git
PKG_SOURCE_VERSION:=dc9747a8208e05d55b68cc6fc923800b319357e0
#PKG_SOURCE_URL:=https://github.com/BeeeOn/gateway-app.git
#PKG_SOURCE_VERSION:=v$(PKG_VERSION)

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_SOURCE_SUBDIR)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DCMAKE_INSTALL_PREFIX=/
CMAKE_OPTIONS += -DPOCO_NO_FLOAT=ON
CMAKE_OPTIONS += -DADAAPP_NO_SYSTEMD=ON

define Package/$(PKG_NAME)
	SECTION:=utils
	CATEGORY:=Utilities
	TITLE:=gateway-app
	DEPENDS:=+poco +libmosquittopp
	URL:=http://beeeon.org
	MAINTAINER:=Matej Postolka <xposto02@stud.fit.vutbr.cz>
endef

define Package/gateway-app/install
	$(INSTALL_DIR) $(1)
	$(CP) -r $(PKG_INSTALL_DIR)/* $(1)
endef

$(eval $(call BuildPackage,gateway-app))
