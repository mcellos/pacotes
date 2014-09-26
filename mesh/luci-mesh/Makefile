include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=luci-mesh
PKG_RELEASE:=1
PKG_VERSION:=1.0

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=luci
  CATEGORY:=LuCI
  TITLE:=11s config for luci
  DEPENDS=+iw +luci
endef

define Build/Prepare
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/model/cbi/admin_network/
	$(INSTALL_BIN) wifi.lua  $(1)/usr/lib/lua/luci/model/cbi/admin_network/wifi.lua
endef

$(eval $(call BuildPackage,$(PKG_NAME))) 
