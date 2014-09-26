include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=ath9k-nohwcrypt
PKG_RELEASE:=1
PKG_VERSION:=1.0

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Disables hwcrypt to run authsae
  DEPENDS=+authsae
endef

define Build/Prepare
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/rc.d/
	$(INSTALL_BIN) S70ath9knohwcrypt $(1)/etc/rc.d/S70ath9knohwcrypt
endef

$(eval $(call BuildPackage,$(PKG_NAME)))