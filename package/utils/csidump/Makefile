include $(TOPDIR)/rules.mk

PKG_NAME:=csidump
PKG_VERSION:=0.1.0
PKG_RELEASE:=5

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE.txt

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/GustavoCuri1501/MtkCSIdump.git
PKG_SOURCE_VERSION:=LAND
PKG_MIRROR_HASH:=skip

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1
CMAKE_INSTALL:=0

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/csidump
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=MediaTek CSI UDP dumper
  URL:=https://github.com/MtkWifiRev/MtkCSIdump
  DEPENDS:=+libnl-tiny +libstdcpp
endef

define Package/csidump/description
 MediaTek CSI collector that streams CSI samples over UDP for external visualization.
endef

define Build/Install
	$(INSTALL_DIR) $(PKG_INSTALL_DIR)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/CSIdump $(PKG_INSTALL_DIR)/usr/bin/CSIdump
endef

define Package/csidump/conffiles
/etc/config/csidump
endef

define Package/csidump/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/CSIdump $(1)/usr/bin/CSIdump

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/etc/init.d/csidump $(1)/etc/init.d/csidump

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/etc/config/csidump $(1)/etc/config/csidump
endef

$(eval $(call BuildPackage,csidump))
